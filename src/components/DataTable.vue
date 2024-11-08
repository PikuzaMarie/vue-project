<template>
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
      fetch('https://retoolapi.dev/wHFLgA/data')
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
.table .profiles {
  border-collapse: collapse;
  width: calc(100vw - 337px);
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
</style>
