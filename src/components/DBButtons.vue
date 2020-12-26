<template>
    <div>
        <H1>DATABASES</H1>
        <button @click="$emit('onclickPersonalData')">PersonalData</button>
        <button @click="$emit('onclickEmployees')">Employees</button>
        <button @click="$emit('onclickPositions')">Positions</button>
        <button @click="$emit('onclickBusinessTrips')">BusinessTrips</button>
    </div>
</template>

<style>
button {
    padding: 50px;
    margin: 10px;
}
</style>