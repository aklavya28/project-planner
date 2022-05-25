<template>
  <div class="filer_nav">
    <input
      type="button"
      @click="showFilter('all')"
      :class="{ active: current === 'all' }"
      value="View All"
    />
    <input
      type="button"
      @click="showFilter('completed')"
      :class="{ active: current === 'completed' }"
      value="Completed"
    />
    <input
      type="button"
      @click="showFilter('ongoing')"
      :class="{ active: current === 'ongoing' }"
      value="Ongoing"
    />
  </div>
</template>

<script>
export default {
  props: ["current"],
  methods: {
    showFilter(by) {
      this.$emit("filterChange", by);

      // console.log(by);
    },
  },
};
</script>

<style scoped>
.filer_nav {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 15px 0;
}

.filer_nav input[type="button"] {
  border: 0;
  background: 0;
  text-transform: uppercase;
  font-weight: bold;
  color: rgb(143, 143, 143);
  font-size: 15px;
  transition: all ease 0.5s;
  cursor: pointer;
}

.filer_nav input[type="button"].active {

  color: #000;
}
</style>
