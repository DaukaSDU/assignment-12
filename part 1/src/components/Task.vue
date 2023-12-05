<template>
<div>
  <span>
    <input :id="task.id" type="checkbox" class="_checkbox" v-model="checked">
    {{ task.text || '' }}
  </span>
  <span @click="sendTask" class="trash">
    <img src="../assets/trash.svg" alt="remove">
  </span>
</div>
</template>

<script>
export default {
    props: {
      task: Object
    },
    data() {
      return {
        checked: this.task.checked || false
      }
    },
    methods: {
      sendTask() {
        this.$emit('remove', this.task)
      }
    },
    watch: {
      checked() {
        this.$emit('check', this.checked)
        console.log('The task <' + this.task.id + '> "' + this.task.text + '" was ' + ((this.checked) ? 'checked' : 'unchecked')) 
      }
    }
}
</script>

<style>
li, li>div {
  display: flex;
  justify-content: space-between;
  list-style: none;
  font-size: 20px;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  width: 100%;
}

li>div>span {
  display: flex;
  align-items: center;
  color: #fff;
}

._checkbox {
  border-radius: 50%;
  outline: none;
  appearance: none;
  border: 2px solid #ff3232;
  width: 1.3rem;
  height: 1.3rem;
  transition: all .1s linear;
  margin: 5px;
  cursor: pointer;
}

._checkbox:hover {
  border-width: 4px;
}

._checkbox:checked {
  background-color: #0dcc0d;
  border-color: #017a01;
}

.trash {
  padding: 5px;
  margin: 5px;
  cursor: pointer;
}
</style>