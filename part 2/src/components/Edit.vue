<template>
<span id="bt_edit">
    <button @click="edit">Edit profile</button>
</span>
<span :class="visable">
    <input id="edit_img" @change="changeProfileImage" type="file" accept="image/*">
    <form @submit.prevent="submit">
        <label>name</label>
        <input v-model="name" type="text" placeholder="name">
        <label>email</label>
        <input v-model="email" type="email" placeholder="email">
        <label>birthday</label>
        <input v-model="birthday" type="date">
        <button>save</button>
    </form>
</span>
</template>

<script>
export default {
    data() {
        return {
            check: false,
            visable: this.check ? 'visable' : 'not-visable',
            name: '',
            email: '',
            src: '',
            birthday: null
        }
    },
    methods: {
        edit() {
            this.check = !this.check
            this.visable = this.check ? 'visable' : 'not-visable'
        },
        submit() {
            if (!this.name || !this.email || !this.birthday) {
                alert('All fields are required!')
                return
            }
            this.$emit('edit_details', { name: this.name, email: this.email, birthday: new Date(this.birthday) })
            this.edit()
        },
        changeProfileImage(event) {
            const input = event.target;
            const image = this.$refs.profileImage;

            if (input.files && input.files[0]) {
                const reader = new FileReader();

                reader.onload = () => {
                    // Set the source of the image to the selected file
                    this.src = reader.result;
                    this.$emit('edit_img', new URL(this.src))
                };

                reader.readAsDataURL(input.files[0]);
            }

        }
    },
    props: {
        curr_img: URL
    }
}
</script>

<style>
#bt_edit>button {
    border: none;
    background: none;
    text-decoration: underline;
    color: green;
    cursor: pointer;
}

.visable {
    display: block;
}

.not-visable {
    display: none;
}

.visable>form>input {
    display: block;
    margin-bottom: 10px;
}
</style>