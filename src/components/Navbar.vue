<template>
  <div class="nav">
    <router-link :to="{ name: 'home' }"> Home</router-link>
    <router-link :to="{ name: 'addProject'}"> Add Project</router-link>
  </div>
</template>

<script>
export default {};
</script>
<style scoped>
.nav {
  display: flex;
  gap: 14px;
  text-transform: uppercase;
  justify-content: center;
  align-items: center;
  font-size: 15px;
  padding: 15px;
  background: #fff;
  margin-bottom: 12px;
  border-radius: 4px;
}

.nav a {
  text-decoration: none;
  color: #747474;
  font-weight: bold;
  transition: all ease 0.5s;
}

.nav a.router-link-active {
  color: #4ebd54;
}
</style>
