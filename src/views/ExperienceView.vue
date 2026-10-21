<script setup>
import { ref } from 'vue'

const experience = [
  {
    role: 'Frontend Developer Intern',
    company: 'Prathibhatheeram Foundation',
    dates: 'June 2026 - Present',
    details: [
      'Build responsive web interfaces using Vue.js, HTML, CSS, and JavaScript.',
      'Collaborate with developers and designers to deliver features from development through deployment.',
      'Use GitHub for version control.'
    ]
  },
  {
    role: 'Process Associate',
    company: 'Amazon',
    dates: 'Dec 2020 - July 2023',
    details: [
      'Resolved 80+ stakeholder requests per month with high data accuracy while consistently meeting and exceeding quality and productivity targets.',
      'Performed root cause analysis to identify defects and operational barriers, and proposed process improvements that increased efficiency.',
      'Documented defects and recommended corrective actions to reduce recurring issues, supporting audit and governance activities.',
    ]
  },
  {
    role: 'Graduate Engineer Trainee',
    company: 'Hindustan Aeronautics Limited',
    dates: 'June 2019 - Sept 2020',
    details: [
      'Coordinated with engineering and quality teams on wiring and testing procedures for aerospace projects.',
      'Inspected loom connector part numbers and ran continuity checks.',
      'Prepared inspection schedules used as authoritative references for compliance.'
    ]
  }
]

const openCompany = ref(null)

function toggleCompany(company) {
  if (openCompany.value === company) {
    openCompany.value = null
  } else {
    openCompany.value = company
  }
}
</script>

<template>
  <div class="experience">
    <h1>Experience</h1>

    <div class="experience-list">

      <div
        v-for="value in experience"
        :key="value.company"
        class="experience-item"
      >

        <button
          class="experience-row"
          @click="toggleCompany(value.company)"
        >

          <div class="company-info">
            <h2>{{ value.company }}</h2>
            <p>{{ value.role }}</p>
          </div>

          <div class="right-side">
            <p class="dates">{{ value.dates }}</p>

            <span
              class="arrow"
              :class="{ open: openCompany === value.company }"
            >
              +
            </span>
          </div>

        </button>

        <div
          v-if="openCompany === value.company"
          class="experience-details"
        >

          <ul>
            <li
              v-for="detail in value.details"
              :key="detail"
            >
              {{ detail }}
            </li>
          </ul>

        </div>

      </div>

    </div>
  </div>
</template>

<style scoped>
.experience {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem 0;
}

h1 {
  margin-bottom: 2rem;
  font-size: 3rem;
  font-family: 'Montserrat', sans-serif;
  font-weight: 800;
}

.experience-item {
  border-bottom: 1px solid rgba(181, 101, 95, 0.22);
}

.experience-row {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem 0;
  border: none;
  background: transparent;
  color: inherit;
  text-align: left;
  cursor: pointer;
  transition: all 0.3s ease;
}

.experience-row:hover {
  background: rgba(181, 101, 95, 0.08);
  padding-left: 1rem;
  padding-right: 1rem;
}

.company-info h2 {
  margin: 0;
  font-size: 1.4rem;
  font-weight: 400;
}

.company-info p {
  margin: 0.4rem 0 0;
}

.right-side {
  display: flex;
  align-items: center;
  gap: 1.5rem;
}

.dates {
  margin: 0;
  white-space: nowrap;
}

.arrow {
  width: 25px;
  font-size: 1.5rem;
  font-weight: 300;
  text-align: center;
  transition: transform 0.3s ease;
}

.arrow.open {
  transform: rotate(45deg);
}

.experience-details {
  max-width: 800px;
  padding: 0 3rem 1.5rem 0;
  animation: fade-in 0.3s ease;
}

.experience-details ul {
  margin: 0;
  padding-left: 1.2rem;
}

.experience-details li {
  margin-bottom: 0.6rem;
  line-height: 1.6;
}

@keyframes fade-in {
  from {
    opacity: 0;
    transform: translateY(-5px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 600px) {
  .experience {
    padding: 1.5rem;
  }

  h1 {
    font-size: 2.5rem;
  }

  .experience-row {
    align-items: flex-start;
    gap: 1rem;
  }

  .right-side {
    gap: 0.5rem;
  }

  .dates {
    font-size: 0.85rem;
    text-align: right;
  }

  .experience-details {
    padding-right: 0;
  }
}
</style>