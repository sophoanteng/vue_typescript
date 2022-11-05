<template>
    <div>
        <p>Order by {{myOrder}}</p>
        <div  v-for="list in sortByOrder" :key="list.id">
             <div class="contain-info">
                <h4>{{list.title}}</h4>
                <p>{{list.salary}}</p>
                <p>{{list.location}}</p>
             </div>
        </div>
    </div>
</template>
<script lang="ts">
import { computed, defineComponent, PropType } from 'vue'
import Job from '@/types/Job'
import OrderList from '@/types/OrderList'

export default defineComponent({
    props: {
        jobInfo: {
            require: true,
            type: Array as PropType<Job[]>
        },
        myOrder: {
            require: true,
            type: String as PropType<OrderList>
        }
    },
    setup(props) {
     const sortByOrder = computed(() => {
       return [...props.jobInfo].sort((a: Job, b: Job) => {
         return a[props.myOrder] > b[props.myOrder] ? 1 : -1
       })
     })
     return {sortByOrder}
    }
})
</script>
<style>
.contain-info{
    background: rgb(241, 210, 210);
    height: 90px;
    padding: 0px 15px 23px;
    width: 800px; 
    text-align: center;
}
.contain-info h4 {
    padding-top: 10px;
}
</style>