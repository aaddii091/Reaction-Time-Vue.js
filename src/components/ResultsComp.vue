<template>
  <div>
    <div class="block" v-if="status">
      <h2>SCORE {{ score }}MS</h2>
    </div>
  </div>
</template>

<script>
export default {
  props: ["score", "status"],
  data() {
    return {
      visible: false,
    };
  },
  methods: {},
};
</script>

<style>
.block {
  width: 50vw;
  padding: 100px 0;
  border: 1px solid rgb(0, 63, 0);
  border-radius: 10px;
  background-color: rgb(47, 224, 255);
  margin: 40px auto;
  text-align: center;
  cursor: pointer;
}
</style>
