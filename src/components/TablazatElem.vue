<template>
        <tr>
            <td v-if="edit">
                <input type="text" v-model="title">
            </td>
            <td v-if="!edit">
                {{ title }}
            </td>

            <td v-if="edit">
                <input type="number" v-model="price">
            </td>
            <td v-if="!edit">
                {{ price }}
            </td>

            <td v-if="edit">
                <input type="number" v-model="quantity">
            </td>
            <td v-if="!edit">
                {{ quantity }}
            </td>
            <td v-if="edit">
                <button @click="Save">Save</button>
            </td>
            <td v-if="!edit">
                <button @click="Delete">X</button>
                <button @click="Edit">Edit</button>
            </td>
        </tr>
</template>

<script>
export default{
    props: ['row'],
    data() {
        return {
            title: this.row.title,
            price: this.row.price,
            quantity: this.row.quantity,
            edit: false
        }
    },
    methods: {
        Delete() {
            this.$emit('row_deleted', {original: this.row})
        },
        Edit() {
            this.edit = true
        },
        Save() {
            this.$emit('row_changed', {
                original: this.row,
                new: {
                    title: this.title,
                    price: this.price,
                    quantity: this.quantity
                }
            })
            this.edit = false
        }
    }
}
</script>