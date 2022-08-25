<template>
  <div
    id="main-container"
    class="border-2 border-orange-500 mx-auto max-w-md mt-8 shadow-orange-300 shadow-sm"
  >
    <h1 class="text-center font-bold text-2xl my-4 text-orange-500">
      {{ title }}
    </h1>
    <Form />
  </div>
</template>

<script>
import Form from "./Form.vue";
export default {
  props: {
    title: String,
  },
  components: {
    Form,
  },
};
</script>

<style>
#main-container {
  background-image: url("../assets/bg-image.avif");
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
