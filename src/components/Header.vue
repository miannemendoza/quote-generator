<template>
  <header>
    <h1>
      {{ title }}
    </h1>
  </header>
</template>

<script>
export default {
  props: ["title"],
};
</script>
 
<style lang="scss">
header {
  // font-size: 20px;
  padding: 16px;
  margin: 16px;
  font-weight: 300;
  display: flex;
  justify-content: center;
  text-transform: uppercase;
  // border-bottom: 1px solid black;
}
</style>
