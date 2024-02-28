<template>
  <ul class="grid grid-cols-3">
    <li v-for="tour in tours" :key="tour.id" class="gap-20 p-2 w-[560px]">
      <img
        :src="tour.image"
        :alt="tour.image"
        class="h-[550px] w-full object-cover rounded-2xl p-2"
      />
      <h2 class="py-4 px-2 text-xl font-semibold">{{ tour.name }}</h2>
      <div>
        <p class="pb-4 px-2">{{ tour.info }}</p>
        <p class="text-2xl font-bold">For only {{ tour.price }}$</p>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  name: "Tour",
  data() {
    return {
      tours: [],
    };
  },
  methods: {
    async fetchData() {
      try {
        const response = await fetch(
          "https://course-api.com/react-tours-project"
        );
        if (!response.ok) {
          throw new Error("Network error");
        }
        const data = await response.json();
        this.tours = data;
        console.log(this.tours);
      } catch (error) {
        console.error("Error fetching data", error);
      }
    },
  },
  mounted() {
    this.fetchData();
  },
};
</script>
