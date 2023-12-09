<script setup>
import { Icon } from '@iconify/vue'
import List from './List.vue'
import { ref, onMounted, computed, watch } from 'vue'


const currentKey = ref(0)
const loderStatus = ref(false)


const filteredValue = ref([])
const todos = ref([])
const chackstatus = ref(true)
const name = ref('')
const val = ref(0)
const input_content = ref('')
const input_category = ref(null)

const todos_asc = computed(() => todos.value.sort((a, b) => {
    return b.createdAt - a.createdAt
}))


const addtodo = () => {
    if (input_category.value.trim() == '' || input_content.value.trim() == '') {
        return
    }

    todos.value.push({
        content: input_content.value,
        category: input_category.value,
        done: false,
        createdAt: new Date().getTime(),
        key: new Date().getTime()
    })

    console.log('ok')
}



watch(todos, newval => {
    localStorage.setItem('todos', JSON.stringify(newval))
}, { deep: true})


const closeSlider = () => {
    loderStatus.value = false
}





const  sendreq  = (data) =>  {
    loderStatus.value = true 

    getDataFromArray.then((data1) => {

    })

}


const testPromis = new Promise((resolve, reject) => {

    resolve('data')
})




const runcode = (value) => {
    document.getElementById('')
    loderStatus.value = true
filteredValue.value =  todos_asc.value.filter((e)=> e.key == value)

    // const getDataFromArray = new Promise((resolve, reject) => {
    //     currentKey.value = value
    //     resolve(currentKey.value)
    // })

    // getDataFromArray.then((data) => {
    //     console.log(data)
    // })

}







// adding scripts for tests for asomething wired

const thatValue = ref(false)

const changeValue = () => {
        thatValue.value = !thatValue.value
}






const getthatDate = (a) => {
    const currentDate = new Date(a)
const month = currentDate.getMonth()
const day = currentDate.getDate()
const year = currentDate.getFullYear()
    return `${day} / ${month} / ${year}`
}










</script>


<template>
    <main>
        <section class="greeting text-center  p-5">
            <div>
                <h1>CREATE A TOOL</h1>
                <form @submit.prevent="addtodo">
                    <div class="row">
                        <div class="col-1"></div>
                        <div class="col-10">
                            <div class="d-flex text-center flex-column">

                                <h4 class="fw-light text-start h5">Whats on your to do list?</h4>
                                <div class="input-group mb-3">
                                    <input type="text" class="form-control p-3" placeholder="e.g. make a video"
                                        v-model="input_content">
                                </div>

                                <h4 class="fw-light text-start h5">Pick a category</h4>
                                <div class="">
                                    <div class="options">

                                        <label>
                                            <input v-model="input_category" type="radio" name="category" id="category"
                                                value="bussiness">
                                            <div>bussiness </div>
                                        </label>

                                        <label>
                                            <input v-model="input_category" type="radio" name="category" id="category"
                                                value="School">
                                            <div>School</div>
                                        </label>

                                        <label>
                                            <input v-model="input_category" type="radio" name="category" id="category"
                                                value="hobby">
                                            <div>hobby</div>
                                        </label>
                                    </div>
                                </div>
                                <input class="btn btn-info" type="submit" value="add to do" />
                            </div>
                        </div>
                        <div class="col-1">
                        </div>
                        
                    </div>
                </form>
                <div v-if="loderStatus" id="slider" class="slider ">
                    <div  @click="closeSlider" class="slider2"></div>
                    <div class="slider1 bg-white">

                        <div @click="closeSlider" class="text-end closer">
                            <Icon icon="carbon:close-filled" width="25" />
                        </div>
                        <div class="text-center mt-4">
                            <h3>Description</h3>
                           
                            <!-- <div v-if="loder == 'true'">
                                <div  class="d-flex pt-5 pb-4 justify-content-center">
                                    <div class="sk-chase">
                                        <div class="sk-chase-dot"></div>
                                        <div class="sk-chase-dot"></div>
                                        <div class="sk-chase-dot"></div>
                                        <div class="sk-chase-dot"></div>
                                        <div class="sk-chase-dot"></div>
                                        <div class="sk-chase-dot"></div>
                                    </div>
                                </div>
                                <div class="">
                                    <div class=" text-center">
                                        <h5 class="fs-6 fw-normal">loading...</h5>
                                        <button @click="makefalse">clld</button>
                                    </div>
                                </div>
                            </div> -->
                            <div>
                                <table>
                                    <div v-for="data in filteredValue" :key="data.key">
                                    </div>
                                    <tbody>
                                        <tr>
                                            <th>Task Name: </th>
                                            <td>{{ filteredValue[0].content }}</td>
                                        </tr>
                                        <tr>
                                            <th>Task details </th>
                                            <td><i>null</i></td>
                                        </tr>
                                        <tr>
                                            <th>Task creation date: </th>
                                            <td>{{getthatDate(filteredValue[0].key) }}</td>
                                        </tr>
                                    </tbody>
                                </table>
                                <div class="d-flex">
                                    <button @click="runcode" class="btn btn-success w-100 m-1">Completed</button>
                                    <button class="btn btn-danger w-100 m-1">Delete</button>
                                </div>
                            </div>

                        </div>
                    </div>
                </div>
                <List  @my-event="runcode" :name="todos_asc" />
            </div>
        </section>
    </main>
</template>