<template>
  <div id="header">
    <img
      src="https://www.riskofrain.com/wp-content/uploads/2019/04/RoR-logo_outlined.png"
      id="logo"
    />
    <input id="searchBar" type="text" placeholder="Search.." />
  </div>
</template>

<script setup></script>

<style scoped>
a {
  color: white;
  text-decoration: none;
  transition: 150ms;
}

a:hover {
  filter: opacity(50%);
}

#searchBar {
  height: 2rem;
  border-radius: 0.3rem;
  padding-left: 0.5rem;
  border: none;
  margin-right: 4rem;
}

#logo {
  height: 75%;
  margin-left: 4rem;
}

#header {
  display: flex;
  justify-content: space-around;
  align-items: center;
  background-color: rgb(19, 19, 19);
  width: 100%;
  height: 100px;
  font-weight: 700;
  box-shadow: rgb(34, 34, 34) 0px 0px 1rem;
  transition: 250ms ease;
  margin-bottom: 1rem;
}
</style>
