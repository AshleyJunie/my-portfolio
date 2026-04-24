<template>
  <div class="hero-section">
    <h1>Welcome to My Portfolio</h1>
    <p>Check out my work and skills.</p>
    <Button @click="downloadCV">Download CV</Button>
  </div>
</template>

<script>
export default {
  methods: {
    downloadCV() {
      const link = document.createElement('a');
      link.href = '/CV.pdf';
      link.download = 'Ashley-CV.pdf';
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link);
    }
  }
};
</script>

<style scoped>
.hero-section {
  text-align: center;
  margin: 20px;
}
</style>
