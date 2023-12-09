<template>
    <div class="row p-4">
        <div class="col-1"></div>
        <div class="col-10">
                <div class="listss" @click="clickbtn(names.key)" v-for="names in name" :key="names.key">
                    <div class="border btn btn-outline-secondary w-100 m-1 p-4">
                        <div>
                        {{ names.content }}
                        </div>
                    </div> 
                </div>
        </div>
        <div class="col-1"></div>
    </div>
</template>

<script>
export default {
    name: "ListComponent",
    props: ['name'],
    methods : {
    throwData(vals) {
        console.log(vals)
    },
    clickbtn(values) {
        this.$emit('myEvent', values)
    }
  }
}
</script>


