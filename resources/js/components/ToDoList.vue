<template>
    <div class="container">
        <h1>To Do</h1>
        <input-form @emit-submit="addList"/>
        <ul class="list">
            <li v-for="(item, index) in list" :key="index">
                {{ item.title }}
                <span class="delete" @click="deleteList(index)">Hapus</span>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    data: function () {
        return {
            list: [
                { title: "menyapu" },
                { title: "cuci piring" },
                
            ],
            input: ""
        }
    },

    methods: {
        addList() {
            let newList = {
                title: datainput,
            }
            this.list.push(newList)
        },
        deleteList(index) {
            this.list.splice(index, 1)
        }
    },
    mounted() {
        console.log("Component Mounted")
    }
}
</script>