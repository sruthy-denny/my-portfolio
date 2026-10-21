<script setup>
    const contacts = [
        {
        label: 'Gmail',
        link: 'mailto:info.sruthydenny@gmail.com'
        },

        {
        label: 'GitHub',
        link: 'https://github.com/sruthy-denny'
        },

        {
        label: 'Resume',
        link: import.meta.env.BASE_URL + 'Sruthy_Denny_Resume.pdf'
        }


    ]
</script>

<template>
  <div>
    <h1>Let's Connect</h1>
    <p class="intro">I'm always happy to chat about projects, ideas, or opportunities.</p>
    <div class="contact-list">
      <a
        v-for="item in contacts"
        :key="item.label"
        :href="item.link"
        class="contact-link"
        :target="item.label === 'Gmail' ? undefined : '_blank'"
        :download="item.label === 'Resume' ? '' : undefined"
        rel="noopener"
      >
        {{ item.label }}
      </a>
    </div>

    <p class="closing">Usually reply within a day.</p>
  </div>
</template>

<style scoped>
  .contact-list {
  display: flex;
  flex-direction: column;
  gap: 1.8rem;
  margin-top: 2.5rem;
}

.contact-link {
  font-size: 2.2rem;
  font-family: 'Montserrat', sans-serif;
  text-decoration: none;
  color: #b5655f;
  width: fit-content;
  transition: transform 0.3s ease, opacity 0.3s ease;
  margin-left: -0.1em;
}

.contact-link:hover {
  transform: translateX(10px);
  opacity: 0.7;
}

.intro {
  font-size: 1.3rem;
  font-family: 'Montserrat', sans-serif;
  margin-top: 1rem;
}

h1 {
  margin-top: 2rem;
  margin-bottom: 0.5rem;
  font-size: 3rem;
  font-family: 'Montserrat', sans-serif;
  font-weight: 800;
}

.closing {
  font-size: 1.1rem;
  font-family: 'Montserrat', sans-serif;
  margin-top: 3rem;
  opacity: 0.7;
}

</style>