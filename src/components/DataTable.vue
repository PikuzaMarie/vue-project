<template>
  <div class="container">
    <div class="header">
      <div class="title">
        <h2>Обработанные</h2>
        <button class="btn transparent">
          <img src="../assets/icons/icon-refresh.svg" alt="icon-refresh" />
        </button>
      </div>
      <div class="actions">
        <button class="btn dropdown">
          Действия <img src="../assets/icons/icon-arrow-down.svg" alt="icon-arrow-down" />
        </button>
        <div>
          <button class="btn option">Добавить</button>
          <button class="btn option">Изменить</button>
          <button class="btn option">Удалить</button>
        </div>
      </div>
    </div>
    <div class="table">
      <table class="profiles">
        <thead>
          <tr>
            <th>Статус</th>
            <th>Имя</th>
            <th>Фамилия</th>
            <th>Компания</th>
            <th>Специальность</th>
            <th>Телефон</th>
            <th>E-mail</th>
            <th>Интересы</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(profile, index) in profiles" :key="index">
            <td>{{ profile.status }}</td>
            <td>{{ profile.firstName }}</td>
            <td>{{ profile.lastName }}</td>
            <td>{{ profile.company }}</td>
            <td>{{ profile.jobTitle }}</td>
            <td>{{ profile.phone }}</td>
            <td>{{ profile.email }}</td>
            <td>{{ profile.interests }}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="footer">
      <p>Количество элементов на странице:</p>
      <div class="custom-select">
        <div class="select-header" @click="toggleDropdown">
          <span>{{ selectedValue }}</span>
          <img src="../assets/icons/icon-arrow-down-gray.svg" alt="icon-arrow-down-gray" />
        </div>

        <div v-if="isOpen" class="select-options">
          <div
            v-for="option in options"
            :key="option"
            class="select-option"
            @click="selectOption(option)"
          >
            {{ option }}
          </div>
        </div>
      </div>
      <span id="page-number">1-1 из 2</span>
      <div class="pagination-buttons">
        <button class="btn transparent">
          <img src="../assets/icons/icon-arrow-left.svg" alt="icon-arrow-left" />
        </button>
        <button class="btn transparent">
          <img src="../assets/icons/icon-arrow-right.svg" alt="icon-arrow-right" />
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      profiles: [],
    }
  },
  mounted() {
    this.fetchProfiles()
  },
  methods: {
    fetchProfiles() {
      fetch('https://retoolapi.dev/wHFLgA/data?_limit=5')
        .then((response) => response.json())
        .then((data) => {
          this.profiles = data
        })
        .catch((error) => {
          console.error('Ошибка при попытке загрузки данных:', error)
        })
    },
  },
}
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  gap: 20px;
  width: 100%;
  padding: 30px 20px 0;
  margin: 10px 40px 20px 10px;
  box-shadow: 0px 4px 9px 0px #00000040;
}
.header {
  display: flex;
  justify-content: space-between;
}
.container .header .title {
  display: flex;
  gap: 15px;
}
.container .table .profiles {
  border-collapse: collapse;
  width: calc(100vw - 337px - 60px);
  padding: 0 30px;
  flex-grow: 1;
}

.table .profiles th,
.table .profiles td {
  padding: 8px;
  text-align: left;
  border-bottom: 1px solid #aaaaaa;
}

.table .profiles th {
  font-weight: 800px;
}

.container .footer {
  display: flex;
  justify-content: flex-end;
  gap: 28px;
  padding: 30px 15px 30px 0;
  margin-top: auto;
  border-top: 1px solid #aaaaaa;
}

.actions {
  position: relative;
  display: inline-block;
}

.dropdown {
  display: flex;
  align-items: center;
  width: fit-content;
  gap: 8px;
  background-color: #0f4c82;
  color: #ffffff;
  padding: 11px 65px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}

.actions div {
  display: none;
  position: absolute;
  top: 100%;
  left: 0;
  background-color: #ffffff;
  border: 1px solid #e0e0e0;
  border-top: none;
  border-radius: 0 0 6px 6px;
  box-shadow: 0px 0px 7px 0px #00000040;
  z-index: 1;
  width: 206px;
  padding: 16px 10px;
}

.actions:hover div {
  display: block;
  top: 90%;
}

.option {
  background: none;
  border: none;
  color: #000000;
  padding: 8px 10px;
  text-align: left;
  cursor: pointer;
  width: 188px;
}

.option:hover {
  background-color: #ededed;
}
</style>
