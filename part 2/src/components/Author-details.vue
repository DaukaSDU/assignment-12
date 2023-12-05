<template>
<div class="author-details">
    <span><span>name:</span> {{ name || '-no date-' }}</span>
    <span><span>email:</span> {{ email || '-no date-' }}</span>
    <span><span>age:</span> {{ age }}</span>
    <span><span>birthday:</span> {{ str_birthday }}</span>
</div>
</template>

<script>
export default {
    data() {
        return {
            // birthday: new Date('2004-11-30')
        }
    },
    props: {
        name: String,
        email: String,
        birthday: Date
    },
    computed: {
        str_birthday() {
            if (!this.birthday) {
                return '-no date-'
            }
            return this.birthday.getDate() + '-' + 
                    (this.birthday.getMonth() + 1) + '-' + 
                    this.birthday.getFullYear() + 'y'
        },
        age() {
            if (!this.birthday) {
                return '-no date-'
            }
            let curr_y = new Date().getFullYear(),
                y = this.birthday.getFullYear()
            let curr_m = new Date().getMonth(),
                m = this.birthday.getMonth()
            let curr_d = new Date().getDate(),
                d = this.birthday.getDate()
            let age = curr_y - y
            age -= (curr_m < m)
            if (curr_m == m) {
                age -= (curr_d < d)
            }
            return age
        }
    }
}
</script>

<style>
.author-details>span {
    display: block;
    padding: 5px;
    font-size: 18px;
}

.author-details>span>span {
    font-weight: bold;
}
</style>