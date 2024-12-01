<script setup>
import { ref, computed } from 'vue'
import AddProjectSubject from './components/AddProjectSubject.vue'
import ProjectSubjectList from './components/ProjectSubjectList.vue'
import ProjectSubjectFilter from './components/ProjectSubjectFilter.vue'

const projectSubjects = ref([
  {
    name: 'Панчарево',
    image: 'https://bulgarianontheroad.com/wp-content/uploads/2024/05/img_0660-min.jpg?w=1024',
    description: 'Пейката с панорамна гледка над Панчарево е една от любимите ми дестинации за кратка уикенд разходка. От нея се открива страхотен изглед към езерото и околността, а преходът е лек и приятен. Голямо предимство на пътеката е и това, че в повечето случаи горе е доста по-спокойно, отколкото ако решите да се разхождате по алеята.',
  },
  {
    name: 'Пасарел',
    image: 'https://bulgarianontheroad.com/wp-content/uploads/2021/06/d18fd0b7d0bed0b2d0b8d180-d0bfd0b0d181d0b0d180d0b5d0bb-3.jpg?w=1024',
    description: 'Язовир Пасарел е разположен в Панчаревския пролом на р. Искър. Въженият мост над него се намира между Панчарево и Долни Пасарел – за ориентир погледнете Google maps, локацията е отбелязана. Може да се ориентирате и спрямо ресторант „Шефс“, който се намира отсреща.',
  },
  {
    name: 'Дядо Йоцо гледа',
    image: 'https://static.pochivka.bg/sights.bgstay.com/images/02/2391/54eba3b3d3666.jpg',
    description: 'Едно от местата, които не бива да пропускате пътувайки през Искърското дефиле е паметникът Дядо Йоцо гледа. Паметникът е изграден през 2005 година. Идеята за издигането му е на Огнян Петров, родом от село Очиндол, а проектът е дело на Георги Тишков и Моника Игаренска. Статуята е висока 5 метра и представя Вазовия герой Дядо Йоцо, вперил незрящ поглед към Искърското дефиле и железницата, която сега минава по маршрута София-Мездра.',
  }
]);

const filteredProjectSubjects = ref([]) 

const addProjectSubject = (newTrail) => {
  projectSubjects.value.push(newTrail) 
  filterProjectSubjects('') 
}

const deleteProjectSubject = (index) => {
  projectSubjects.value.splice(index, 1) 
  filterProjectSubjects('') 
}

const filterProjectSubjects = (filterText) => {
  if (!filterText) {
    filteredProjectSubjects.value = projectSubjects.value
  } else {
    filteredProjectSubjects.value = projectSubjects.value.filter(subject =>
      subject.name.toLowerCase().includes(filterText.toLowerCase())
    )
  }
}

filterProjectSubjects('')
</script>

<template>
  <div id="app">
    <div class="main-container">
      
      <header class="header">
        <img src=".\components\icons\mountains.png" alt="Mountain" class="header-image" />
        <h1>Mountain day</h1>
      </header>

      <div class="filter-section">
        <ProjectSubjectFilter @filter-trails="filterProjectSubjects" />
      </div>
      
      <div class="content-container">

          <AddProjectSubject @add-trail="addProjectSubject" />

        <ProjectSubjectList
          :projectSubjects="filteredProjectSubjects"
          @delete="deleteProjectSubject"
        />
        
      </div>
    </div>
  </div>
</template>


<style scoped>

html, body {
  height: 100%; 
  margin: 0;    
  padding: 0;   
}

.main-container {
  height: 100vh;
  width: 100%;
  display: flex;
  flex-direction: column;
} 

.header {
  background: linear-gradient(to right, #a5d6a7, #81c784);
  padding: 20px;
  text-align: center;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  margin-bottom: 20px;
  display: flex;
  position: fixed;
  top: 0;
  width: 100vw;
}

.header h1 {
  font-family: 'Brush Script MT', cursive, bold;
  font-weight: bold;
  font-size: 2rem;
  color: #2e7d32; /* Dark green color */
  letter-spacing: 1px;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1); /* Soft text shadow */
  margin-left: 30px;
}

.header-image {
  width: 50px; 
  height: auto;
}

.filter-section {
  text-align: left;
  margin-bottom: 10px;
}

.content-container {
  padding: 0 20px;
  display: flex;
  justify-content: space-between;
  gap: 20px;
  align-items: start;
}

.project-subject-list {
  flex-grow: 1;
  padding: 20px 0;
}

form {
  width: 400px; 
  background-color: #f0f9f0; 
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

</style>
