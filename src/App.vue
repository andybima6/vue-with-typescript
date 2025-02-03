<template>
  <div class="app">
    <button @click="handleClick('title')">order by title</button>
    <button @click="handleClick('salary')">order by salary</button>
    <button @click="handleClick('location')">order by location</button>
    <JobList :jobs="jobs" :order="order" />
    <!-- <p>{{ name }} - {{ age }}</p>
    <button @click="changeName('Zelda')">change name</button>
    <button @click="changeAge('30')">change age</button> -->
    <!-- <p>{{ jobs[1].location }}</p> -->
  </div>
</template>

<script lang="ts">
import { reactive, ref, toRefs } from "vue";
import JobList from "./components/JobList.vue";
import Job from "./types/job";
import OrderTerm from "./types/OrderTerm";

export default ({  
  name: "App",
  components: { JobList },

  setup() {
    // Cara 1
    // const state = reactive({
    //   // Membuat objek state yang reaktif
    //   name: "Link", // Properti name dengan nilai string 'Link'
    //   age: 25 as number | string, // Properti age yang bisa berupa number atau string
    // });

    // return { ...toRefs(state) }; // Menggunakan toRefs agar setiap properti menjadi reaktif secara individual

    // Cara 2
    // Variabel reaktif 'name' dengan nilai awal "Link"
    // const name = ref("Link"); // Menyimpan nama dalam variabel reaktif

    // // Variabel reaktif 'age' yang bisa berisi angka atau string, nilai awal 25
    // const age = ref<number | string>(25); // Menyimpan usia dalam variabel reaktif

    // return { name, age };

    const jobs = ref<Job[]>([
      // Mendeklarasikan variabel reaktif `jobs` yang berisi daftar pekerjaan sebagai array objek
      { title: "farm worker", location: "Lon Lon Ranch", salary: 30000, id: "1" }, // Pekerjaan di peternakan
      { title: "quarryman", location: "Death Mountain", salary: 40000, id: "2" },
      { title: "flute player", location: "The Lost Woods", salary: 35000, id: "3" },
      { title: "fisherman", location: "Lake Hylia", salary: 21000, id: "4" },
      { title: "prison guard", location: "Gerudo Valley", salary: 32000, id: "5" },
    ]);

    const order = ref<OrderTerm>("title"); // Mendeklarasikan variabel reaktif `order` dengan nilai awal "title", digunakan untuk menentukan urutan pengurutan pekerjaan

    const handleClick = (term: OrderTerm) => {
      // Fungsi yang mengubah nilai `order` berdasarkan parameter yang diterima
      order.value = term; // Mengubah nilai `order` sesuai dengan term yang dipilih
    };

    return { jobs, order, handleClick }; // Mengembalikan objek yang berisi jobs, order, dan handleClick agar dapat digunakan dalam komponen
  },
});

// methods: {
// changeName(name: string) {  // Mendefinisikan metode `changeName` yang menerima parameter `name` dengan tipe data `string`
//   this.name = name;  // Mengubah nilai properti `name` di dalam instance komponen menjadi nilai yang diterima sebagai parameter
//   return name;  // Mengembalikan nilai `name` yang baru
// },
// changeAge(age: number | string) {
//   this.age = age;
//   return age;
// },
//   },
// });
</script>

<style>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
