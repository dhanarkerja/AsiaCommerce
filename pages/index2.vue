<template>
  <Child
    @callTest="test"
  />
</template>

<script>
import Child from "../components/Child.vue";

export default ({
  name: "Parent",

  components: {
    Child,
  },

  methods: {
    test() {
      alert("Test");
    },
  }
});
</script>