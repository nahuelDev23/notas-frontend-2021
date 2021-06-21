<template>
    <h1>notas</h1>
    <div v-for="item in notas" :key="item.id">
        {{item.title}}
        <div v-if="item.favorite">
            <i class="fas fa-bookmark"></i>
            
        </div>
        <div v-else>
            <i class="far fa-bookmark"></i>
        </div>
         <div v-for="(x,index) in JSON.parse(item.ingredients)" :key="index">
             {{ x.name }}
         </div>
         <div v-for="(x,index) in item.categories" :key="index">
             <li>{{ x }}</li>
         </div>
    </div>
</template>

<script>
export default {
    data(){
        return {
            notas: []
        }
    },
    methods:{
        getNotas(){
            const config = {
                 headers:{
                    token:"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJkYXRhIjp7InJvbCI6IkFETUlOIiwiYWN0aXZvIjp0cnVlLCJfaWQiOiI2MGNmYWJiN2M0YzhiNzBhNGMxNWRkYjYiLCJuYW1lIjoiMTExMSIsImVtYWlsIjoibmFodWVsQGdtYWlsLmNvbSIsImRhdGUiOiIyMDIxLTA2LTIwVDIwOjU3OjI3LjkxMFoiLCJfX3YiOjB9LCJpYXQiOjE2MjQyODQ4MjksImV4cCI6MTYyNjg3NjgyOX0.00CYB495fBugZslMXvpmy5QXHIdfaxMnr7TMy2WOvks"
                } 
            }
            this.axios.get("/my-notes",config)
            .then(res=>{
                this.notas = res.data
            })
        }
    },
    created(){
        this.getNotas()
    }
}
</script>

<style>

</style>