<template>
  <div class="modal" v-if="show" @click.stop="close">
    <div @click.stop class="model_content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "mymodel",
  props: {
    show: {
      type: Boolean,
      deafault: false,
    },
  },
  methods: {
    close() {
      this.$emit("update:show", false);
    },
  },
};
</script>

<style>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 9999;
  display: flex;
}
.model_content {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 300px;
  height: 200px;
  background-color: #fff;
  border-radius: 5px;
  padding: 20px;
}
</style>
