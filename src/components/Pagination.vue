<template>
    <div>
        <button @click="$emit('onClickLeft')">LEFT</button>
        <button @click="$emit('onClickRight')">RIGHT</button>
    </div>
</template>

<style scoped>
button {
    padding: 5px;
    margin: 10px;
}
</style>