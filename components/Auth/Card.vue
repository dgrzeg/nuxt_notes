<template>
  <div>
    <NCard class="card">
      <h3>{{ authStateText }}</h3>
      <div class="input-container">
        <input type="email" placeholder="Email" />
        <input type="password" placeholder="Password" />
      </div>
      <NButton>Submit</NButton>
      <p @click="toggleAuthState">{{ authStateParagraphText }}</p>
    </NCard>
  </div>
</template>

<script setup lang="ts">
const authState = ref<'login' | 'signup'>('login')

const toggleAuthState = () =>
  authState.value === 'login'
    ? (authState.value = 'signup')
    : (authState.value = 'login')

const authStateText = computed(() =>
  authState.value === 'login' ? 'Login' : 'Signup'
)
const authStateParagraphText = computed(() =>
  authState.value === 'login'
    ? "Don't have an aaccount? Create one now"
    : 'Already have an account? Login'
)
</script>

<style scoped>
.card {
  padding: 1rem;
  width: 25rem;
}
.card h3 {
  font-size: 1.75rem;
  text-transform: capitalize;
}
.input-container {
  display: flex;
  flex-direction: column;
}
.input-container input {
  margin-bottom: 0.3rem;
  padding: 0.2rem;
  outline: none;
  border: 0.1rem solid rgba(0, 0, 0, 0.1);
  border-radius: 0.2rem;
}
p {
  color: lightgrey;
  font-size: 0.5rem;
  cursor: pointer;
}
</style>
