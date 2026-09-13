<template>
<transition name="fade">
    <div class="promo">
      <span>It's your lucky day! Get an extra cup of Mocha for $4.</span>
      <div>
  <div class="cup" :class="{ 'disabled-hover' : disabled }">
      <div class="cup-body" :aria-label="coffee.name" :class="{ 'disabled-hover' : disabled, bigger: false }" :data-test="coffee.name.replace(' ', '_')" :data-cy="coffee.name.replace(' ', '-')">
        <div
          v-for="ingredient in coffee.recipe"
          :key="ingredient.name"
          :class="['ingredient', ingredient.name, 'disabled-hover']"
          :style="{ height: ingredient.quantity + '%'}"
        >{{ ingredient.quantity ? ingredient.name : '' }}</div>
      </div>
      <div class="cup-handler" :class="{ 'disabled-hover' : disabled }"></div>
    </div>
      </div>
      <div class="buttons">
        <button class="yes" @click="addToCart(coffee.name); close();">Yes, of course!</button>
        <button @click="close()">Nah, I'll skip.</button>
      </div>

    </div>
  </transition>
</template>

<script lang="ts">
import { defineComponent } from "vue";

import { mapMutations } from "vuex";

export default defineComponent({
  name: "Promotion",
  emits: ['close'],
  data() {
    return {
      coffee: {
        "name": "(Discounted) Mocha",
        "price": 4,
        "discounted": true,
        "recipe": [
            { "name": "espresso", "quantity": 30 },
            { "name": "chocolate syrup", "quantity": 20 },
            { "name": "steamed milk", "quantity": 25 },
            { "name": "whipped cream", "quantity": 25 }
        ]
    },
      disabled: true
    };
  },
  methods: {
    ...mapMutations("cart", ["addToCart"]),
    close() {
      this.$emit('close');
    }
  },
});

</script>

<style scoped>
.buttons {
  display: flex;
  grid-gap: 10px;
}

.buttons button {
  min-width: 160px;
  border: 2px solid black;
}

.yes {
  background: rgb(198, 218, 181);
}

.promo {
  display: flex;
  justify-items: center;
  align-items: center;
  flex-direction: column;
  grid-gap: 16px;
  font-size: larger;
  border: 4px solid black;
  padding: 10px;
  margin-inline: 20px;
  text-align: center;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>

<style scoped>
.cup {
  display: flex;
  will-change: transform;
}

.cup-body {
  width: 200px;
  height: 180px;
  border: 6px solid black;
  display: flex;
  flex-direction: column-reverse;
  border-radius: 0px 0px 20px 20px;
  overflow: hidden;
}

.cup-body.bigger {
  height: 240px;
  width: 220px;
}

.cup-handler {
  width: 30px;
  height: 72px;
  margin-top: 18px;
  background-color: initial;
  border-bottom-right-radius: 100px;
  border-top-right-radius: 100px;
  border: 8px solid black;
  border-left: 0;
  box-sizing: border-box;
}

.cup:hover {
  cursor: pointer;
  transform: rotate(-4deg);
}

.cup:hover .cup-body {
  border-color: goldenrod;
}

.cup:hover .cup-handler {
  border-color: goldenrod;
}

.ingredient {
  display: flex;
  justify-content: center;
  align-items: center;
}

.disabled-hover {
  pointer-events: none;
  border-color: initial;
}

.disabled-hover:hover {
  pointer-events: none;
  border-color: black;
}

/* recipe */

.espresso {
  background-color: rgb(222, 98, 38);
}

.milk.foam {
  background-color: rgb(198, 218, 181);
}

.steamed.milk {
  background-color: rgb(178, 187, 140);
}

.steamed.cream {
  background-color: rgb(239, 238, 217);
}

.chocolate.syrup {
  background-color: rgb(154, 128, 69);
}

.whipped.cream {
  background-color: rgb(183, 221, 220);
}

.water {
  background-color: rgb(127, 195, 179);
}
</style>
