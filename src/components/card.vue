<template>
  <div id="cards" v-if="cardData">
    <div id="card" v-for="data in cardData" :key="data">
      <h2 id="title">{{ data.title }}</h2>
      <h3 id="rarity">{{ data.rarity }}</h3>
      <div id="descriptions">
        <p>{{ data.description.textDescription }}</p>
        <p>{{ data.description.advancedDescription }}</p>
      </div>
      <h2>STATS</h2>
      <div id="columns">
        <div id="column1">
          <p v-for="item in formatStats(data.stats)[0]" :key="item">
            {{ item }}
          </p>
        </div>
        <div id="column2">
          <p v-for="item in formatStats(data.stats)[1]" :key="item">
            {{ item }}
          </p>
        </div>
      </div>
    </div>
  </div>
  <div v-else>
    <p>Loading...</p>
  </div>
</template>

<script setup>
import axios from "axios";
import { ref, onMounted } from "vue";

const cardData = ref(null);
onMounted(() => {
  axios.get("/api/items/passive/all").then((response) => {
    cardData.value = response.data?.sort(function (a, b) {
      var textA = a.title.toUpperCase();
      var textB = b.title.toUpperCase();
      return textA < textB ? -1 : textA > textB ? 1 : 0;
    });
  });
});

function formatStats(data) {
  let column1 = [];
  let column2 = [];
  const objectKey = Object.keys(data);
  for (let i = 0; i < objectKey.length; i++) {
    const disassembled = data[objectKey[i]];
    const objectKey2 = Object.keys(disassembled);
    if (typeof disassembled === "string") {
      column1.push(`${objectKey[i]}: ${disassembled}`);
      continue;
    }
    column1.push(`${objectKey[i]}: ${disassembled[objectKey2[0]]}`);
    column2.push(`${objectKey[i]}: ${disassembled[objectKey2[1]]}`);
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
  height: 458px;
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
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  width: inherit;
  gap: 16px;
  height: 100%;
  margin-bottom: 16px;
}

#column1 > p,
#column2 > p {
  border-bottom: 1px rgba(0, 0, 0, 0.2) solid;
  padding-bottom: 0.1rem;
}
</style>
fit-content
