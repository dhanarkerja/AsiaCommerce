<template>
  <button @click="$emit('callTest')">Click Me</button>
</template>

<script>

    
export default ({
  name: "Child",
});
</script>