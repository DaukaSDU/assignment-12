<script>
import Logo from './components/Author-logo.vue'
import Detail from './components/Author-details.vue'
import Greet from './components/Greeting-msg.vue'
import Edit from './components/Edit.vue'

export default {
    components: {
        Logo,
        Detail,
        Greet,
        Edit
    },
    methods: {
        edit_details(user) {
            this.name = user.name
            this.email = user.email
            this.birthday = user.birthday
        }
    },
    data() {
        return {
            name: 'Daulet',
            email: 'dauletomarov1130@gmail.com',
            birthday: new Date('2004-11-30'),
            logo_src: new URL('https://images.unsplash.com/photo-1575936123452-b67c3203c357?q=80&w=1000&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8aW1hZ2V8ZW58MHx8MHx8fDA%3D'),
            grt_msg: 'admin'
        }
    }
}
</script>

<template>
<Logo :src="logo_src" />
<div>
    <Greet :msg="grt_msg" />
    <Detail :name="name" :email="email" :birthday="birthday" />
</div>
<Edit @edit_img="(data) => logo_src = data" @edit_details="edit_details" />
</template>

<style>
* {
    margin: 0px;
    padding: 0px;
    box-sizing: border-box;
}

#app {
    max-width: 1000px;
    margin: 20px auto;
    display: flex;
    justify-content: space-around;
    padding: 10px;
    border: 2px solid green;
}
</style>