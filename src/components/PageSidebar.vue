<template>
  <div class="sidebar">
    <div class="sidebar-content">
      <div class="select-title">
        <h3>Профили</h3>
        <img src="../assets/icons/icon-arrow-up.svg" alt="icon-arrow-up" />
      </div>
      <div class="options">
        <nav>
          <ul>
            <li :class="{ active: activeTab === 'all' }" @click="selectTab('all')">
              <div class="circle">
                <img src="../assets/icons/icon-tick.svg" alt="icon-.svg" />
              </div>
              <h4>Все</h4>
            </li>
            <li :class="{ active: activeTab === 'processed' }" @click="selectTab('processed')">
              <div class="circle">
                <img src="../assets/icons/icon-tick.svg" alt="icon-tick" />
              </div>
              <h4>Обработанные</h4>
            </li>
            <li :class="{ active: activeTab === 'pending' }" @click="selectTab('pending')">
              <img src="../assets/icons/icon-pending.svg" alt="icon-pending" />
              <h4>Не обработанные</h4>
            </li>
          </ul>
        </nav>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    activeTab: String,
  },
  methods: {
    selectTab(tab) {
      this.$emit('activeTab', tab)
    },
  },
}
</script>

<style scoped>
.sidebar {
  width: 337px;
  height: calc(100vh - 60px);
  background-color: #ffffff;
  box-shadow: 0px 4px 9px 0px #00000040;
}
.sidebar-content {
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 32px 35px 0 28px;
}
.circle {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 25px;
  height: 25px;
  border-radius: 25px;
  background-color: #0f4c82;
}
.select-title {
  display: flex;
  gap: 177px;
}
ul {
  list-style-type: none;
}
li {
  display: flex;
  gap: 20px;
  cursor: pointer;
}
li:not(:last-child) {
  margin-bottom: 27px;
}
.active {
  color: #0f4c82;
}
</style>
