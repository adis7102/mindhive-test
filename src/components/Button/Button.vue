<template>
  <div class="button">
    <img v-if="withAppleICon" class="apple-image" src="@/assets/images/Apple_logo_white.svg.png" alt="icon" />
    <p>{{ title }}</p>
  </div>
</template>

<script>
export default {
  name: 'button',
  props: ['withAppleICon', 'title', 'backgroundColor', 'color', 'width', 'height']
}
</script>

<style scoped>
.button {
  width: v-bind(width);
  height: v-bind(height);
  background-color: v-bind(backgroundColor);
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

.apple-image {
  width: 17px;
  height: auto;
  margin-right: 5px;
}

p {
  margin: 0;
  font-size: 24px;
  font-weight: 500;
  color: v-bind(color);
}
</style>