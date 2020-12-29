<template>
    <div>
        <h2>{{dbName}}</h2>
        <table class="tbl">
            <TableElement
                v-for="(data, index) in dbData" :key="index"
                v-bind:data="data"
                v-bind:dbName="dbName"
            />
        </table>
    </div>
</template>

<script>
import TableElement from '@/components/TableElement'
export default {
    props: ['dbData', 'dbName'],
    components: {
        TableElement
    }
}
</script>

<style scoped>
.tbl {
  margin-left: auto;
  margin-right: auto;
}
</style>