<template>
  <div id="header">
    <img
      src="https://www.riskofrain.com/wp-content/uploads/2019/04/RoR-logo_outlined.png"
      id="logo"
      width="175px"
    />
    <div id="URLs">
      <a href="#">Home</a>
      <a href="#">Items</a>
      <a href="#">About</a>
      <input id="searchBar" type="text" placeholder="Search.." />
    </div>
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
}

#header {
  display: flex;
  justify-content: space-around;
  align-items: center;
  background-color: rgb(25, 89, 133);
  width: 100%;
  height: 100px;
  font-weight: 700;
  letter-spacing: 0.1rem;
  font-size: 1.3rem;
  box-shadow: rgb(25, 89, 133) 0px 0px 0.5rem;
  transition: 250ms ease;
  margin-bottom: 1rem;
}

#URLs {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 3rem;
}
</style>
