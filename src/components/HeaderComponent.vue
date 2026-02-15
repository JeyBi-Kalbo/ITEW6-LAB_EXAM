<template>
  <header class="header">
    <div class="logo">🎓 Student Info</div>
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/students">Students</router-link>
    </nav>
  </header>
</template>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 40px;
  background: white;
  box-shadow: 0 4px 12px rgba(0,0,0,0.08);
}

.logo {
  font-size: 20px;
  font-weight: 600;
  color: #2c3e50;
}

nav a {
  margin-left: 20px;
  text-decoration: none;
  font-weight: 500;
  color: #555;
}

nav a.router-link-active {
  color: #42b883;
}
</style>
