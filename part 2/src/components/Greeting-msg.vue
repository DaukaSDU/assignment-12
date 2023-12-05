<template>
<span id="greet-msg">your position: <span>{{ msg || '-no date-' }}</span></span>
</template>

<script>
export default {
    data() {
        return {
            // msg: 'admin'
        }
    },
    props: {
        msg: String
    }
}
</script>

<style>
#greet-msg {
    display: block;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    padding: 5px;
}

#greet-msg>span {
    font-weight: bold;
    color: rgb(42, 200, 42);
}
</style>