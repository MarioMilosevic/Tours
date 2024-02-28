<template>
    <Heading />
  </template>
  
  <script>
  import Heading from "./components/Heading.vue";
  
  export default {
    name: "App",
    data() {
      return {
        title: "My First Vue App",
      };
    },
    methods: {
     async handleClick() {
        const response = await fetch("https://course-api.com/react-tours-project")
        console.log(response)
      },
    },
    components: {
      Heading,
    },
  };
  </script>
  