<script >
// import List from './List.vue'

export default {
    name: "Home",
    components: {
        List
    },
    data: {
        todos: [],
        name: '',
        val: 0,
        input_content: '',
        input_category: null,
    },
    methods: {
        todos_asc: computed(() => todos.value.sort((a, b) => {
            return b.createdAt - a.createdAt
        }))
    }
}
</script>

<template>
    <main>
        <section class="greeting text-center  p-5">


            <!-- for for adding data to the array -->

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
                                        <input type="radio" name="category" id="category" value="bussiness"
                                            v-model="input_category">
                                        <div>bussiness</div>
                                    </label>

                                    <label>
                                        <input type="radio" name="category" id="category" value="School"
                                            v-model="input_category">
                                        <div>School</div>
                                    </label>

                                    <label>
                                        <input type="radio" name="category" id="category" value="hobby"
                                            v-model="input_category">
                                        <div>hobby {{ name }}</div>
                                    </label>
                                </div>
                            </div>
                            <input class="btn btn-info" type="submit" value="add to do" />
                        </div>
                    </div>
                    <div class="col-1"></div>

                </div>
            </form>
            <div id="slider" class="slider ">
                <div class="slider2" @click="closeSlider"></div>
                <div class="slider1 bg-white">

                    <div @click="closeSlider" class="text-end closer">
                        <Icon icon="carbon:close-filled" width="25" />
                    </div>
                    <div class="text-center mt-4">
                        <h3>Description</h3>
                        <div class="d-flex pt-5 pb-4 justify-content-center">
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
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <List @my-event="sendreq" :name="todos_asc" />
        </section>
    </main>
</template>

