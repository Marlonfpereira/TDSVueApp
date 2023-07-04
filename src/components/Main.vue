<template>
  <main>
    <ItemList class="lista" :item-list="itens"></ItemList>
    <InputItem @newItem="addItem"></InputItem>
  </main>
</template>

<style scoped>
main {
  box-sizing: border-box;
  display: grid;
  grid-template-rows: 1fr 0fr;
  min-height: 80vh;
  max-height: 80vh;
  margin: 0;
  max-width: 2000px;
  padding: 1em;
}
.lista {
  overflow-y: scroll;
  max-height: 480px;
  margin: 1em;
}
</style>

<script>
import InputItem from './InputItem.vue'
import ItemList from './ItemList.vue'

export default {
  name: 'Main',
  data () {
    return {
      itens: []
    }
  },
  components: { InputItem, ItemList },
  methods: {
    addItem (item) {
      this.itens.push(item)
    }
  }
}
</script>
