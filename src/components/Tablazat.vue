<template>
<div>
    <table>
        <tr>
            <th>Cím</th>
            <th>Ár</th>
            <th>Mennyiség</th>
            <th>Operations</th>
        </tr>
        <TablazatElem
        v-for="row in rows"
        v-bind:key="row.title"
        v-bind:price="row.price"
        v-bind:quantity="row.quantity"
        :row="row"
        @row_changed="Change"
        @row_deleted="Delete"/>
        <tr>
            <td>
                <input type="text" v-model="title">
            </td>
            <td>
                <input type="number" v-model="price">
            </td>
            <td>
                <input type="number" v-model="quantity">
            </td>
            <td>
                <button @click="Submit">Submit</button>
            </td>
        </tr>
    </table>
</div>
</template>

<script>
import TablazatElem from './TablazatElem.vue'
export default{
    props: ['rows'],
    components: {TablazatElem},
    data() {
        return {
            title: "",
            price: "",
            quantity: ""
        }
    },
    methods: {
        Submit() {
            this.$emit('row_added', {title: this.title, price: this.price, quantity: this.quantity})
        },
        Change(e) {
            this.$emit('row_changed', e)
        },
        Delete(e) {
            this.$emit('row_deleted', e)
        }
    }
}
</script>