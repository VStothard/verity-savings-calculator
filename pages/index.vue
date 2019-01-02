<template>
  <section class="container">
    <div>
      <ExpenseGroup group-name="Everyday Expenses" :expense-array="everydayExpenses" @groupTotal="calcExpenseTotal"/>
      <ExpenseGroup group-name="Fun Money" :expense-array="funExpenses" @groupTotal="calcExpenseTotal" />
    </div>
  </section>
</template>

<script>
import ExpenseGroup from '~/components/ExpenseGroup'

export default {
  components: {
    ExpenseGroup
  },
  data() {
      return {
        totalExpenses: 0,
        groupTotals: [],
        everydayExpenses: [
          {
            isEditable: false,
            itemName: 'first treat',
            itemDesc: 'the first thing',
            itemVal: 2000
          }, 
          {
            isEditable: false,
            itemName: 'second treat',
            itemDesc: 'the second thing',
            itemVal: 2000
          },
        ],
        funExpenses: [
            {
              isEditable: false,
              itemName: 'first treat',
              itemDesc: 'the first thing',
              itemVal: 2000
            },
            {
              isEditable: false,
              itemName: 'second treat',
              itemDesc: 'the second thing',
              itemVal: 2000
            },
            
        ]
      }
    },
    methods: {
      calcExpenseTotal(value) {
        //todo: if group is already present, update, else push
        
        this.groupTotals.push({
          groupName: value.groupName,
          expensesTotal: value.expensesTotal
        });
        console.log(this.groupTotals, 2000);
      }
    }
}
</script>