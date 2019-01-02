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
                <span v-if="!item.isEditable" @click="editToggle(item)">{{item.itemName}}</span>
                <input v-else type="text" v-model="item.itemName" @keyup.enter="editToggle(item)" />
            </div>
            <div class="w-1/4 p-4">
                <span v-if="!item.isEditable" @click="editToggle(item)">{{item.itemDesc}}</span>
                <input v-else type="text" v-model="item.itemDesc" @keyup.enter="editToggle(item)" />
            </div>
            <div class="w-1/4 p-4">
                <span v-if="!item.isEditable" @click="editToggle(item)">{{item.itemVal}}</span>
                <input v-else type="number" v-model="item.itemVal" @keyup.enter="editToggle(item)" />
            </div>
            <button type="button" @click="item.isEditable = !item.isEditable" class="w-1/4 text-left p-4">{{ item.isEditable ? 'SAVE' : 'EDIT' }}</button>
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
    methods: {
        groupTotal(a) {
            const values = a.map(item => parseInt(item.itemVal));
            return values.reduce((accumulator, currentValue) => accumulator + currentValue);
        },
        editToggle(item) {
            item.isEditable = !item.isEditable
        }
    }
}
</script>