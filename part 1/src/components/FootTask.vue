<template>
<span id="container">
    <span>completed: {{ number.completed || 0 }}</span>
    <span>all: {{ number.all || 0 }}</span>
    <span>uncompleted: {{ number.uncompleted || 0 }}</span>
</span>
</template>

<script>
export default {
    props: {
        number: Object
    }
}
</script>

<style>
#container {
    color: #fff;
    width: 100%;
    display: flex;
    justify-content: space-between;
}

#container>span {
    text-transform: uppercase;
    border: 1px solid #fff;
    padding: 5px;
}
</style>