<script>
export default {
    data() {
        return {
            operators: ['+', '-', '*', '/', '%'],
            x: 0,
            y: 0,
            selectedOp: '+'
        }
        
    },
    computed: {
        result() {
            switch (this.selectedOp) {
                case '+':
                    return this.x + this.y
                case '-':
                    return this.x - this.y
                case '*':
                    return this.x * this.y
                case '/':
                    return this.y !== 0 ? this.x / this.y : 'Error (Division by 0)'
                case '%':
                    return this.y !== 0 ? this.x % this.y : 'Error (mod 0)'
                default:
                    return 'Invalid operator'
            }
        }
    }
}
</script>

<template>
    <p>x <input v-model.number="x"></p>
    <select v-model="selectedOp">
        <option v-for="op in operators">{{ op }}</option>
    </select>
    <p>y <input v-model.number="y"></p>

    <p>---------------------</p>

    <p>= {{ result }}</p>
</template>

<style scoped>
p,
input {
    font-family: monospace;
}

p {
    white-space: pre;
}
</style>
