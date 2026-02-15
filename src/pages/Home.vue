<template>
  <div class="container">
    <div class="welcome-card">
      <h1>Welcome to Student Info App</h1>
      <p>
        This modern Vue 3 application demonstrates component usage,
        props and state management, client-side routing,
        and API data integration.
      </p>

      <router-link to="/students" class="cta-btn">
        View Students
      </router-link>
    </div>
  </div>
</template>

<style scoped>
.welcome-card {
  background: white;
  padding: 50px 40px;
  border-radius: 16px;
  box-shadow: 0 8px 24px rgba(0,0,0,0.08);
  text-align: center;
  max-width: 750px;
  margin: 80px auto;
}

.welcome-card h1 {
  font-size: 32px;
  margin-bottom: 20px;
  color: #2c3e50;
}

.welcome-card p {
  color: #555;
  margin-bottom: 30px;
  line-height: 1.6;
}

.cta-btn {
  display: inline-block;
  background: #42b883;
  color: white;
  padding: 12px 28px;
  border-radius: 10px;
  text-decoration: none;
  font-weight: 500;
  transition: 0.3s;
}

.cta-btn:hover {
  background: #369870;
}
</style>
