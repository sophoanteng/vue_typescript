<!-- <template>
  <div>
    <h3>{{name}}</h3>
    <button type="submit" @click="changeName('sokphorn teng')">change name</button>
    <h3>{{age}}</h3>
    <button @click="changeAge(24)">change age</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'App',
   data() {
     return {
      name: 'flower-Romdul',
      age: 18 as string | number
     }
   },
   methods: {
    changeName( name: string ){
      this.name = name
      return name
    },
    changeAge(age: string | number){
      this.age = age
      return age
    }
   }
});
</script> -->
//////////////////////////////////////////////////
<!-- <template>
  <div>
    <h3>{{name}}</h3>
    <button type="submit" @click="changeName('sokphorn teng')">change name</button>
    <h3>{{age}}</h3>
    <button @click="changeAge(24)">change age</button>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs } from 'vue';

export default defineComponent({
  name: 'App',
   setup() {   
   const state = reactive({
    name: 'flower-Romdul',
    age: 18 as string | number
   })
   return {...toRefs(state)}
   },
   methods: {
    changeName( name: string ){
      this.name = name
      return name
    },
    changeAge(age: string | number){
      this.age = age
      return age
    }
   }
});
</script> -->
//////////////////////////////////////////////////
<!-- 
<template>
  <div>
    <h3>{{name}}</h3>
    <button type="submit" @click="changeName('sokphorn teng')">change name</button>
    <h3>{{age}}</h3>
    <button @click="changeAge(24)">change age</button>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'App',
   setup() {   
     const name = ref('flower-Romdul')
     const age = ref<number | string>(18)

     return {name, age}
   },
   methods: {
    changeName( name: string ){
      this.name = name
      return name
    },
    changeAge(age: string | number){
      this.age = age
      return age
    }
   }
});
</script> -->
//////////////////////////////////////////////////
<!-- 
<template>
  <div>
    <h3>{{ jobs[4].location}}</h3>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from './types/Job'

export default defineComponent({
  name: 'App',
   setup() {   
    const jobs = ref<Job[]>([
      {title : 'farm worker', location: 'Cambodia', salary: 500, id: '1'},
      {title : 'programer', location: 'French', salary: 400, id: '2'},
      {title : 'Technical', location: 'USA', salary: 300, id: '3'},
      {title : 'Finance', location: 'Korea', salary: 500, id: '4'},
      {title : 'farm', location: 'Thailand', salary: 600, id: '5'},
      {title : 'worker', location: 'Vienam', salary: 700, id: '6'},
      {title : 'Leader', location: 'Singapore', salary: 600, id: '7'},
      {title : 'studying', location: 'Russain', salary: 800, id: '8'},
      {title : 'frontend developer', location: 'Italy', salary: 700, id: '9'},
    ])
    return {jobs}
   },
});
</script> -->
//////////////////////////////////////////////////
<template>
  <div>
    <!-- <h3>{{ jobInfo[4].location}}</h3> -->
    <button @click="clickOrder('title')">Order by title</button>
    <button @click="clickOrder('salary')">Order by salary</button>
    <button @click="clickOrder('location')">Order by location</button>
    <JobList :jobInfo = 'jobInfo' :myOrder="myOrder" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from './types/Job'
import OrderList from './types/OrderList'
import JobList from './components/JobList.vue'

export default defineComponent({
  name: 'App',
  components: {
    JobList
  },
   setup() {   
    const jobInfo = ref<Job[]>([
      {title : 'farm worker', location: 'Cambodia', salary: 500, id: '1'},
      {title : 'programer', location: 'French', salary: 400, id: '2'},
      {title : 'Technical', location: 'USA', salary: 300, id: '3'},
      {title : 'Finance', location: 'Korea', salary: 500, id: '4'},
      {title : 'farm', location: 'Thailand', salary: 600, id: '5'},
      {title : 'worker', location: 'Vienam', salary: 700, id: '6'},
      {title : 'Leader', location: 'Singapore', salary: 600, id: '7'},
      {title : 'studying', location: 'Russain', salary: 800, id: '8'},
      {title : 'frontend developer', location: 'Italy', salary: 700, id: '9'},
    ])
    
    const myOrder = ref<OrderList>('title')
    const clickOrder = (term: OrderList) => {
       myOrder.value = term
    }

    return {jobInfo, clickOrder, myOrder}
   },
});
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
