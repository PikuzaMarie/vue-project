<template>
  <div class="header">
    <div class="burger">
      <span></span>
      <span></span>
      <span></span>
    </div>
    <div>
      <img src="../assets/icons/icon-search.svg" alt="icon-search" />
    </div>
  </div>
</template>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 30px;
  width: 100%;
  height: 60px;
  background-color: #0f4c82;
}
.burger {
  display: flex;
  flex-direction: column;
  gap: 4px;
}
.burger span {
  width: 40px;
  height: 6px;
  border-radius: 25px;
  opacity: 0px;
  background-color: #ffffff;
}
</style>
