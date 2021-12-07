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
        :row="row"/>
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
        }
    }
}
</script>