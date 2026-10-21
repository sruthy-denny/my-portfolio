<script setup>
const projects = [
    {
        title: 'Weather App',
        description: 'A weather app built with Vue.js and Vite. Search a city to see current weather conditions.',
        link: 'https://sruthy-denny.github.io/weatherapp/',
        github: 'https://github.com/sruthy-denny/weatherapp',
    },

    {
         title: 'Timer App',
         description: 'A simple timer app built with Vue.js. Set a time and watch it count down.',
         link: 'https://sruthy-denny.github.io/timerapp/',
         github: 'https://github.com/sruthy-denny/timerapp',       
    },

    {
          title: 'Tic Tac Toe',
          description: 'A Tic Tac Toe game built with Vue.js. Play against a friend on the same device, or challenge the computer.',
          link: 'https://sruthy-denny.github.io/tictactoe/',
          github: 'https://github.com/sruthy-denny/tictactoe',    
    },  
    
    {
          title: 'Todo App',
          description: 'A simple to-do list app built with Vue.js. Add, complete, and delete tasks.',
          link: 'https://sruthy-denny.github.io/todo-app/', 
          github: 'https://github.com/sruthy-denny/todo-app',   
    },    


]
</script>

<template>
    <div>
        <h1>Personal Experiments</h1>
        <div class="project-grid">
        <div v-for="project in projects" :key="project.title" class="project-card">
            
            <h2>{{  project.title }}</h2>
            <p>{{ project.description }}</p>
            <a :href="project.link" target="_blank" rel="noopener">View project</a>
            <a :href="project.github" target="_blank" rel="noopener">View code</a>        
        </div>
        </div>
    </div>
</template>

<style scoped>

    .project-grid {
    display: grid;
    gap: 1.5rem;
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
    }
    
    .project-card {
    border: 1px solid #ccc;
    border-radius: 8px;
    padding: 1rem;
    transition: all 0.3s ease;
    }

    .project-card:hover {
    background: rgba(181, 101, 95, 0.08);
    transform: translateY(-3px);
    }

    h1 {
    margin-top: 2rem;
    margin-bottom: 1.5rem;
    font-size: 3rem;
    font-family: 'Montserrat', sans-serif;
    font-weight: 800;
    }

    a {
    display: inline-block;
    padding: 0;
    margin-right: 1.5rem;
    margin-top: 0.5rem;
    }   
</style>