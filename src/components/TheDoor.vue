<template>
    <div class="door-area">
        <div class="door-frame" :class="{ selected: selected && !open }">
            <the-gift v-if="open && hasGift"/>
        </div>
        <div class="door" @click="selected = !selected" :class="{ open }">
            <div class="number" :class="{ selected }">{{ number }}</div>
            <div class="knob" :class="{ selected }" @click.stop="open = true"></div>
        </div>
    </div>
</template>

<script>
import TheGift from "./TheGift.vue";

export default {
  name: "TheDoor",
  components: { TheGift },
  props: {
      number: {},
      hasGift: { type: Boolean }
  },
  data() {
      return {
          open: false,
          selected: false
      }
  },
};
</script>

<style>
:root {
    --door-border: 5px solid brown;
    --selected-border: 5px solid yellow;
}

.door-area {
    position: relative;
    width: 200px;
    height: 310px;
    border-bottom: 10px solid #aaa;
    margin-bottom: 20px;
    font-size: 3rem;

    display: flex;
    justify-content: center;
}

.door-frame {
    position: absolute;
    height: 300px;
    width: 180px;

    border: var(--door-border);
    border-bottom: none;

    display: flex;
    justify-content: center;
    align-items: flex-end;
}

.door {
    position: absolute;
    top: 5px;
    height: 295px;
    width: 170px;
    background-color: chocolate;

    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
}

.door .knob {
    height: 20px;
    width: 20px;
    border-radius: 10px;
    background-color: brown;
    align-self: flex-start;
    margin-top: 60px;
}

.door-frame.selected {
    border: var(--selected-border);
    border-bottom: none;
}

.door .number.selected {
    color: yellow;
}

.door .knob.selected {
    background-color: yellow;
}

.door.open {
    background-color: #0007;
}

.door.open .number {
    display: none;
}

.door.open .knob {
    display: none;
}
</style>
