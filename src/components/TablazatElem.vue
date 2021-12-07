<template>
        <tr>
            <td>
                {{ title }}
            </td>
            <td>
                {{ price }}
            </td>
            <td>
                {{ quantity }}
            </td>
            <td>
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
            quantity: this.row.quantity
        }
    },
    methods: {
        Delete() {
            this.$emit('row_deleted', {original: this.row})
        },
        Edit() {

        }
    }
}
</script>