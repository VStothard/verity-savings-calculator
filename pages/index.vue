<template>
  <section class="container">
    <div>
      <ExpenseGroup group-name="Everyday Expenses" :expense-array="everydayExpenses" />
      <ExpenseGroup group-name="Fun Money" :expense-array="funExpenses" />
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
    }
}
</script>