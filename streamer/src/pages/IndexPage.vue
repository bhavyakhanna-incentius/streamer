<template>
  <q-page class="h-96 w-full overflow-hidden" style="backgroundColor:#100720" ><!--style="backgroundColor:#03001C;"
     <div class="text-3xl" style="color:#5B8FB9;">SEARCH WHAT YOU MAY</div> -->
     <!-- <img class="w-full" src="../assets/istockphoto-517128364-170667a.jpg" alt="Blackboard" > -->
     <div style="backgroundColor:#31087B;" class="h-16 nav flex justify-between">
      <span class="flex justify-between" style="margin-top: -5px;">
        <span><img class="h-10 mr-2 rounded-lg" src="../assets/devil-s-goat-head-for-metal-rock-band-logo-artwork-vector.jpg" alt="Workflow" ></span>
        <span class="text-3xl font-bold text-blue" >GOAT</span>
      </span>
      <div class="">
        
        <ul class="menu">
          <li class="font-bold text-blue mr-6 mt-1 text-lg" style="font-family: Georgia, serif;">
          <a href="#">Home</a>
        </li>
        <li class="font-bold text-blue text-lg mt-1 mr-6" style="font-family: Georgia, serif;">
          <a href="#">Movies</a>
        </li>
        <li class="font-bold text-blue mr-6 mt-1 text-lg" style="font-family: Georgia, serif;">
          <a href="#">Popular Movies</a>
        </li>
        <li class="font-bold text-blue mr-6 mt-1 text-lg" style="font-family: Georgia, serif;">
          <a href="#">TV Series</a>
        </li>
        <li class="font-bold text-blue mr-3 mt-1 text-lg" style="font-family: Georgia, serif;">
          <a href="#">Anime</a>
        </li>
        <!-- <label for="default-search" class="mb-2 text-sm font-medium text-gray-900 sr-only dark:text-white">Search</label>
        <div class="relative mr-8">
            <div class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none">
                <svg aria-hidden="true" class="w-5 h-5 dark:text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg>
            </div>
            <input type="search" id="default-search" class="block w-full p-2 text-sm text-gray-900 border border-gray-300 bg-gray-50 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500." required>
        </div> -->
      </ul>
      
      </div>
  </div>
        <div class="question-mark "  v-for="item in questionMarks" :key="item" :style="{top:item.y + 'px',left:item.x + 'px'}"> 
          <span style="fontSize:180px;padding:-1000px;solor:#00bfff; text-shadow: 4px 4px #ff00ff;font-family:Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;">?</span>
        </div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'IndexPage',
  data () {
    return {
      startTime: Date.now(),
      questionMarks: [],
    }
  },
  mounted(){
    this.questionMarks = Array.from({ length: 19}, (_, i) => ({
        x: Math.random() * window.innerWidth,
        y: Math.random() * window.innerHeight,
        angle: Math.random() * Math.PI * 2,
        speed: .00000000000000000000004,
      }))
      this.animationLoop()
  },
  methods: {
      animationLoop() {
        requestAnimationFrame(this.animationLoop)

        const elapsed = Date.now() - this.startTime
        this.questionMarks.forEach(questionMark => {
          questionMark.x += Math.cos(questionMark.angle) 
          questionMark.y += Math.sin(questionMark.angle) 

          if (questionMark.x < 0 || questionMark.x > window.innerWidth) {
            questionMark.angle = Math.PI - questionMark.angle
          }

          if (questionMark.y < 0 || questionMark.y > window.innerHeight) {
            questionMark.angle = -questionMark.angle
          }
        })
      },

    },
})
</script>
<style>
  #app {
    position: relative;
    height: 100vh;
  }
  
  .question-mark {
    position: absolute;
    color: #000;
  }
  .nav {
    display: flex;
    align-items: center;
    background-color: #3d3d3d;
    box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.3);
    padding: 20px;
  }
  .menu {
    list-style: none;
    margin: 0;
    padding: 0;
    display: flex;
  }

</style>
