<template>
<img id="profileImage" :src="src || 'https://images.unsplash.com/photo-1575936123452-b67c3203c357?q=80&w=1000&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8aW1hZ2V8ZW58MHx8MHx8fDA%3D'" alt="Profile Image">
</template>

<style>
img {
    width: 20%;
    height: 20%;
}
</style>

<script>
export default {
    props: {
        src: URL
    }
}
</script>