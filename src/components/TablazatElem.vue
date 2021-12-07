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
                <button @clickX="Delete">X</button>
                <button @clickEdit="Edit">Edit</button>
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
}
</script>