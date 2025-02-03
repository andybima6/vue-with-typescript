<template>
  <div class="app">
    <p>{{ name }} - {{ age }}</p>
    <button @click="changeName('Zelda')">change name</button>
    <button @click="changeAge('30')">change age</button>

    <!-- <p>{{ jobs[1].location }}</p> -->
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref, toRefs } from "vue";
import Job from "./types/job";

export default defineComponent({
  name: "App",
  components: {},

  setup() {
    // Cara 1
    const state = reactive({
      // Membuat objek state yang reaktif
      name: "Link", // Properti name dengan nilai string 'Link'
      age: 25 as number | string, // Properti age yang bisa berupa number atau string
    });

    return { ...toRefs(state) }; // Menggunakan toRefs agar setiap properti menjadi reaktif secara individual

    // Cara 2
    // Variabel reaktif 'name' dengan nilai awal "Link"
    // const name = ref("Link"); // Menyimpan nama dalam variabel reaktif

    // // Variabel reaktif 'age' yang bisa berisi angka atau string, nilai awal 25
    // const age = ref<number | string>(25); // Menyimpan usia dalam variabel reaktif

    // return { name, age };

    // const jobs = ref<Job[]>([
    //   // Mendeklarasikan sebuah variabel `jobs` yang berupa ref (reactive state) berisi array dengan tipe data `Job[]`
    //   { title: "farm worker", location: "lon lon ranch", salary: 30000, id: "1" }, // Objek pertama dalam array, berisi data pekerjaan "farm worker" di "lon lon ranch" dengan gaji 30.000
    //   { title: "quarryman", location: "death mountain", salary: 40000, id: "2" },
    //   { title: "flute player", location: "the lost woods", salary: 35000, id: "3" },
    //   { title: "fisherman", location: "lake hylia", salary: 21000, id: "4" },
    //   { title: "prison guard", location: "gerudo valley", salary: 32000, id: "5" },
    // ]);

    // return { jobs };
  },
  methods: {
    changeName(name: string) {  // Mendefinisikan metode `changeName` yang menerima parameter `name` dengan tipe data `string`
      this.name = name;  // Mengubah nilai properti `name` di dalam instance komponen menjadi nilai yang diterima sebagai parameter
      return name;  // Mengembalikan nilai `name` yang baru
    },
    changeAge(age: number | string) {
      this.age = age;
      return age;
    },
  },
});
</script>

<style></style>
