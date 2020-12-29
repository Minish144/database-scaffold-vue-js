<template>
    <div>
        <tr>
            <td>
                <TableRow
                    v-bind:data="data"
                    v-on:onClickDelete="del()"
                />
            </td>
        </tr>
    </div>
</template>

<script>
import TableRow from '@/components/TableRow'
export default {
    props: ['data', 'dbName'],
    components: {
        TableRow
    },
    methods: {
        async del() {
            console.log(this.dbName, this.data.id);
            await fetch(`http://localhost:5000/api/${this.dbName}/${this.data.id}/delete`, {
                method: 'DELETE',
            });
        }
    }
}
</script>

<style scoped>
button {
    margin: 0;
    padding: 0;
}
</style>