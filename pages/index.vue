<template>
  <section class="container">
    <div>
      <ExpenseGroup :expense-array="everydayExpenses" />
      <ExpenseGroup :expense-array="funExpenses" />
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
                    itemName: 'first treat',
                    itemDescription: 'the first thing',
                    value: 2000
                }, 
              {
                    itemName: 'first treat',
                    itemDescription: 'the first thing',
                    value: 2000
                },
            ],
            funExpenses: [
                {
                    itemName: 'first treat',
                    itemDescription: 'the first thing',
                    value: 2000
                },
                {
                    itemName: 'second treat',
                    itemDescription: 'the second thing',
                    value: 2000
                },
                
            ]
        }
    }
}
</script>