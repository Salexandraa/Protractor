<template>
  <div class="container">
    <div>
      <h1>{{ title }}</h1>
    </div>
    <div>
      <ol>
        <li v-for="(item, ind) in listDishes" :key="ind" :v-model="selectedDish">
          {{ item.name }}
          <button class="checkIn" @click="orderDish()">
            Замовлено
          </button>
        </li>
      </ol>
    </div>
    <hr />
    <div>
      <h1>{{ title2 }}</h1>
    </div>
    <div>
      <ol>
        <li v-for="(item, ind) in listDishesPrepare" :key="ind">
          {{item.name}}
          <button class="checkIn" @click="$emit('prepare', index)">
            Приготовлено
          </button>
        </li>
      </ol>
    </div>
  </div>
</template>

<script>
export default {
  name: "Reserved",
  props: {
    listDishes: {
      type: Array,
      default: () => [],
    },
    listDishesPrepare: {
      type: Array,
      default: () => [],
    },
    title: {
      type: String,
      default: "",
    },
    title2: {
      type: String,
      default: "",
    },
    },
    data() {
        return {
            selectedDish: ''
        }
    },
    methods: {
        orderDish() { 
             this.listDishesPrepare.push(this.listDishes)
        }
  },
};
</script>

<style lang="css" scoped>
.container {
  width: 300px;
  height: 500px;
  border: 2px solid;
  border-radius: 15px;
  background-color: skyblue;
}
.checkIn {
  background-color: wheat;
}
</style>
