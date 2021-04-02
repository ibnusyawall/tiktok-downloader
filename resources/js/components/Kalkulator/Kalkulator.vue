<template>
    <div class="container">
        <form  class="text-center" style="margin-top: 20%">
            <h1 class="text-center">Kalc Vue App</h1>
            <input type="number" v-model.number="angka_1"> +
            <input type="number" v-model.number="angka_2">
        </form>
        <h2 class="text-center">{{ angka_1 + angka_2}}</h2>
    </div>
</template>

<script>
    export default {
        data: function() {
            return { angka_1: 0, angka_2: 0 }
        }
    }
</script>
