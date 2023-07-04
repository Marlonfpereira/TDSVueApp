<template>
  <input type="text" name="newItem" id="newItem" @keyup.enter="addItem" placeholder="Adicionar Item" class="bg-secondary-subtle">
</template>

<style scoped>
#newItem {
  align-self: end;
  border: none;
  border-radius: 10px;
  justify-self: center;
  min-height: 2em;
  min-width: 30em;
  padding: .5em;
}

#newItem:focus {
  outline: none;
}
</style>

<script>
import { Item } from '../models/item.js'
export default {
  name: 'InputItem',
  methods: {
    addItem ($event) {
      let valor = $event.target.value
      let item = new Item()
      item.nome = valor
      item.quant = 1
      item.complete = false
      this.$emit('newItem', item)
      $event.target.value = ''
    }
  }
}
</script>
