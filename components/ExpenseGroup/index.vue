<template>
    <div>
        <!-- <ExpenseRow /> -->
        hello {{expenseArray}}
        <!-- <div v-for="(item, i) in expenses" :key="i">
            {{item.itemName}}
        </div> -->
    </div>
</template>
<script>
export default {
    props: {
        expenseArray: {
            type: Array
        }
    },
    computed: {
        expenses() {
            return this.expenseArray
        }
    }
}
</script>