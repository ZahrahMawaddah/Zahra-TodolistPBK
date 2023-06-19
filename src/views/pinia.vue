<template>
  <div class="pencapaian-form">
    <h2>Form Pengisian Pencapaian Target Belajar</h2>
    <form @submit.prevent="submitForm">
      <div class="form-group">
        <label for="item">Item Pelajaran :</label>
        <input type="text" id="item" v-model="item" required />
      </div>
      <div class="form-group">
        <label for="quantity">Bobot beban pembelajaran :</label>
        <input type="number" id="quantity" v-model="quantity" required />
      </div>
      <div class="form-group">
        <label for="minute">Durasi Belajar (menit) :</label>
        <input type="number" id="minute" v-model="minute" required />
      </div>
      <button type="submit">Add to Pinia Stored</button>
    </form>
    <br>
    <br>
    <br>
    <h2>Data Pencapaian Target Belajar</h2>
        <div class="table-header">
          <span>Item Pelajaran</span>
          <span>Bobot Beban Pembelajaran</span>
          <span>Durasi Belajar (menit)</span>
      </div>
    <ul>
      <li v-for="(achievement, index) in achievements" :key="index" class="table-row">
          <span>{{ achievement.item }}</span>
          <span> {{ achievement.quantity }}</span>
          <span>{{ achievement.minute }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      item: "",
      quantity: 0,
      minute: 0,
      achievements: [] // Array untuk menyimpan data pencapaian target belajar
    };
  },
  methods: {
    submitForm() {
      // Validasi data
      if (this.item === "" || this.quantity <= 0 || this.minute <= 0) {
        alert("Mohon lengkapi semua field dengan benar.");
        return;
      }

      // Simpan data pencapaian target belajar ke dalam array
      const achievementItem = {
        item: this.item,
        quantity: this.quantity,
        minute: this.minute
      };
      this.achievements.push(achievementItem);

      // Reset form setelah submit
      this.item = "";
      this.quantity = 0;
      this.minute = 0;

      alert("Item berhasil ditambahkan ke Pencapaian Target Belajar");
    }
  }
};
</script>


<style>
.pencapaian-form {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 20px;
}

.form-group {
  margin-bottom: 1rem;
}

label {
  font-weight: bold;
}

input {
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 100%;
}

button {
  padding: 0.5rem 1rem;
  background-color: #3f51b5;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  margin-top: 10px;
  width: 100%;
}

h2 {
  margin-bottom: 1rem;
  text-align: center;
}

ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

li {
  margin-bottom: 10px;
  padding: 10px;
  border: 1px solid;
  border-radius: 4px;
  background-color: #87CEFA;
  
}

li strong {
  display: inline-block;
  width: 180px;
}

.table-header {
  font-weight: bold;
  display: flex;
  justify-content: space-between;
  border-bottom: 1px solid #ccc;
  padding-bottom: 5px;
  margin-bottom: 10px;
}

.table-header span {
  width: 180px;
}

.table-row {
  display: flex;
  justify-content: space-between;
}

.table-row span {
  width: 180px;
}
</style>
