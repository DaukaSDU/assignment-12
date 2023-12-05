<template>
    <form @submit.prevent="sendTask">
        <select v-model="completed" id="select">
            <option value="false">not completed</option>
            <option value="true">completed</option>
        </select>
        <input v-model="text" id="add_input" type="text" placeholder="Write ...">
        <button>ADD</button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            text: '',
            completed: 'false'
        }
    },
    methods: {
        sendTask() {
            this.$emit('add', { text: this.text, checked: this.completed === 'true' })
            this.text = ''
        }
    },
}
</script>

<style>
form {
    width: 100%;
    display: flex;
    justify-content: center;
    padding: 10px;
    gap: 10px;
}

select {
    color: #fff;
    border: none;
    outline: none;
    background-color: black;
}

#add_input {
    border: none;
    background-color: black;
    border-bottom: 2px solid #fff;
    outline: none;
    color: #fff;
    padding: 5px;
    width: 200px;
    font-size: 20px;
}

#add_input::placeholder {
  color: #828282;
}

button {
    border: 2px solid #fff;
    background-color: black;
    color: #fff;
    padding: 5px;
    border-radius: 10px;
    cursor: pointer;
}
</style>