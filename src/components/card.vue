<template>
  <div id="cards">
    <div id="card">
      <h2></h2>
      <h2 id="title">{{ data.title }}</h2>
      <h3 id="rarity">{{ data.rarity }}</h3>
      <div id="descriptions">
        <p>{{ data.description }}</p>
      </div>
      <h2>STATS</h2>
      <div id="columns">
        <div id="column1">
          <p v-for="item in formatStats(data)[0]" :key="item">
            {{ item }}
          </p>
        </div>
        <div id="column2">
          <p v-for="item in formatStats(data)[1]" :key="item">
            {{ item }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import axios from "axios";
import { ref, onMounted, toRefs } from "vue";

const data = ref("");

onMounted(() => {
  axios.get("/api/items/passive/common/011").then((response) => {
    data.value = response.data;
  });
});

function formatStats(data) {
  let column1 = [];
  let column2 = [];
  const objectKey = Object.keys(data);
  for (let i = 0; i < objectKey.length; i++) {
    const disassembled = data[objectKey[i]];
    const objectKey2 = Object.keys(disassembled);
    column1.push(`${objectKey[i]}: ${disassembled[objectKey2[0]]}`);
    column2.push(`${objectKey[i]}: ${disassembled[objectKey2[1]]}`);
    if (typeof disassembled === "string") {
      column1.push(`${objectKey[i]}: ${disassembled}`);
      break;
    }
  }
  return [column1, column2];
}
</script>

<style scoped>
p,
h1,
h2,
h3,
h4,
h5,
h6 {
  overflow-wrap: break-word;
  padding: 0;
  margin: 0;
  margin-bottom: 0.2rem;
}

#card {
  width: 15rem;
  height: 19.5rem;
  border: 0.15rem solid black;
  border-radius: 0.4rem;
  padding: 1rem;
}

#columns {
  display: flex;
  flex-direction: row;
  gap: 1rem;
}

#cards {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}

#column1 > p,
#column2 > p {
  border-bottom: 1px rgba(0, 0, 0, 0.2) solid;
  padding-bottom: 0.1rem;
}
</style>
