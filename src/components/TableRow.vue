<template>
    <td>
        {{data}} <button @click="$emit('onClickDelete')">x</button>
    </td>
</template>

<script>
export default {
    props: ['data']
}
</script>

<style scoped>
button {
    margin: 0;
    padding: 0;
}
</style>