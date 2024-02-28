<template>
  <Heading />
  <Tour/>
</template>

<script>
import Heading from "./components/Heading.vue";
import Tour from "./components/Tour.vue"
export default {
  name: "App",
  data() {
    const tours = [];
    return {
      tours,
    };
  },
  methods: {
    createTours(data) {
      this.tours = data;
    },
  },
  components: {
    Heading,
    Tour
  },

  mounted() {
    const fetchData = async () => {
      try {
        // setLoading(true);
        const response = await fetch(
          "https://course-api.com/react-tours-project"
        );
        if (!response.ok) {
          throw new Error("Network error");
        }
        const data = await response.json();
        this.createTours(data);
        console.log(this.tours);
        // setTours(data);
      } catch (error) {
        console.error("Error fetching data", error);
      } finally {
        // setLoading(false);
      }
    };
    fetchData();
  },
};
</script>
