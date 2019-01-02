<template>
    <div>
        <h3 class="my-4">{{groupName}}</h3>
        <div class="flex justify-between text-left font-semibold">
            <div class="w-1/4 p-4">Name</div>
            <div class="w-1/4 p-4">Description</div>
            <div class="w-1/4 p-4">Amount</div>
            <div class="w-1/4 p-4">Edit</div>
        </div>
        <div v-for="(item, i) in expenseArray" :key="i" class=" border-b flex justify-between text-left">
            <div class="w-1/4 p-4">
                <span v-if="!item.isEditable" >{{item.itemName}}</span>
                <input v-else type="text" v-model="item.itemName" @keyup.enter="editToggle(item)" />
            </div>
            <div class="w-1/4 p-4">
                <span v-if="!item.isEditable" >{{item.itemDesc}}</span>
                <input v-else type="text" v-model="item.itemDesc" @keyup.enter="editToggle(item)" />
            </div>
            <div class="w-1/4 p-4">
                <span v-if="!item.isEditable">{{item.itemVal}}</span>
                <input v-else type="number" v-model="item.itemVal" @keyup.enter="editToggle(item)" />
            </div>
            <button type="button" @click="editToggle(item)" class="w-1/4 text-left p-4">{{ item.isEditable ? 'SAVE' : 'EDIT' }}</button>
        </div>
        <div class="mt-4"><p>TOTAL: {{groupTotal(expenseArray)}}</p></div>  
    </div>
</template>
<script>
export default {
    props: {
        groupName: {
            type: String
        },
        expenseArray: {
            type: Array
        }
    },
    data() {
        return {
            expensesTotal: 0
        }
    },
    methods: {
        groupTotal(a) {
            let values = a.map(item => parseInt(item.itemVal));
            this.expensesTotal = values.reduce((accumulator, currentValue) => accumulator + currentValue);
        },
        editToggle(item) {
            console.log('yes');
            this.$emit('groupTotal', {
                groupName: this.groupName,
                groupTotal: this.expensesTotal
            });
            item.isEditable = !item.isEditable;
        }
    }
}
</script>