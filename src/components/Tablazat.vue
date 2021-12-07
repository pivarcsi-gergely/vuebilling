<template>
<div>
    <table>
        <tr>
            <th>Cím</th>
            <th>Ár</th>
            <th>Mennyiség</th>
        </tr>
        <TablazatElem
        v-for="row in rows"
        v-bind:key="row.title"
        :row="row"/>
    </table>
</div>
</template>

<script>
import TablazatElem from './TablazatElem.vue'
export default{
    props: ['rows'],
    components: {TablazatElem},
    data() {
        
    },
}
</script>