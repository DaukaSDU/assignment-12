<script>
// import { remove } from '@vue/shared'
import Task from './components/Task.vue'
import AddTask from './components/AddTask.vue'
import FootTask from './components/FootTask.vue'

let id = 1
export default {
    components: {
    Task,
    AddTask,
    FootTask
},
    data() {
        return {
            tasks: []
        }
    },
    methods: {
        remove(task) {
            this.tasks = this.tasks.filter(t => t != task)
        },
        add(task) {
            this.tasks.push({ id: id++, text: task.text, checked: task.checked })
        }
    },
    computed: {
        filtered() {
            return this.tasks.sort((t1, t2) => t1.checked - t2.checked)
        }
    }
}
</script>

<template>
<AddTask @add="add" />
<ul>
    <li v-for="task in filtered" :key="task.id">
        <Task :task="task" @remove="remove" @check="() => task.checked = !task.checked" />
    </li>
</ul>
<FootTask :number="function() {
                        let completed = 0, 
                            uncompleted = 0
                        filtered.forEach(t => {
                            if (t.checked) completed++
                            else uncompleted++
                        })
                        return { 
                            completed: completed, 
                            all: completed + uncompleted, 
                            uncompleted: uncompleted 
                        }
                    }()" />
</template>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    max-width: 1000px;
    margin: auto;
    background-color: black;
}
</style>