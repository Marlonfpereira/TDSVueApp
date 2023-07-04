<template>
  <div class="lista">
    <div class="item bg-secondary-subtle" v-for="item in itemList" :key="item.nome">
      <div class="flex data">
        <input @click="completeItem(item)" v-model="item.complete" type="checkbox" name="complete" id="complete">
        <p :class="{'completo': item.complete}" class="nome">{{ item.nome }}</p>
      </div>
      <div class="flex">
        <div class="flex quant noselect">
          <button @click="subQuant(item)">-</button>
          <p>{{ item.quant }}</p>
          <button @click="addQuant(item)">+</button>
        </div>
        <img @click="deleteItem(item)" class="lixo" src="../assets/trash.svg" alt="trashBin">
      </div>
    </div>
  </div>
</template>

<style scoped>
.lista {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.item {
  align-items: center;
  border-radius: 10px;
  box-sizing: border-box;
  display: flex;
  justify-content: space-between;
  margin: .3em 0;
  min-width: 27em;
  padding: .5em 1em;
  text-align: center;
  width: 50%;
}
.flex {
  display: flex;
}
.data {
  align-items: center;
}
#complete {
  height: 25px;
  margin-right: 1em;
  width: 25px;
}
.nome {
  font-weight: bold;
}
.completo {
  text-decoration: line-through;
  font-weight: 200;
}
.quant {
  align-items: center;
  background-color: rgb(190, 190, 190);
  border-radius: 20px;
  height: fit-content;
  padding: .3em;
}
.noselect {
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.quant button {
  background-color: rgb(190, 190, 190);
  border: none;
  border-radius: 20px;
  height: 25px;
  font-size: large;
  transition: .1s ease-in-out;
  width: 25px;
}
.quant button:hover {
  background-color: rgb(200, 200, 200);
}
.quant button:active {
  background-color: rgb(220, 220, 220);
}
p {
  margin: 0;
}
.quant p {
  width: 25px;
}
.lixo {
  background-color: rgb(190, 190, 190);
  border-radius: 20px;
  margin-left: .8em;
  padding: .3em;
  transition: .1s ease-in-out;
  width: 25px;
}
.lixo:hover {
  background-color: rgb(200, 200, 200);
}
.lixo:active {
  background-color: rgb(220, 220, 220);
}
</style>

<script>
export default {
  name: 'ItemList',
  props: ['itemList'],
  methods: {
    completeItem (item) {
      item.complete = !item.complete
      if (!item.complete && item.quant === 0) {
        item.quant++
      }
    },
    addQuant (item) {
      item.quant++
      if (item.quant !== 0) {
        item.complete = true
        this.completeItem(item)
      }
    },
    subQuant (item) {
      if (item.quant > 1) {
        item.quant--
      } else if (item.quant === 1) {
        item.quant--
        item.complete = false
        this.completeItem(item)
      }
    },
    deleteItem (item) {
      console.log(this.itemList.indexOf(item))
      this.itemList.splice(this.itemList.indexOf(item), 1)
    }
  }
}
</script>
