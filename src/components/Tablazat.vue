<template>
<div>
    <table>
        <th>
            <td>Cím</td>
            <td>Ár</td>
            <td>Mennyiség</td>
        </th>
        <TablazatElem :row="row"/>
    </table>
</div>
</template>

<script>
import TablazatElem from './TablazatElem.vue'
export default{
    props: [''],
    components: {TablazatElem},
    data() {
        
    },
}
</script>