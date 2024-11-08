<template>
  <header>
    <PageHeader />
  </header>
  <main>
    <div class="main-container">
      <Sidebar :activeTab="activeTab" @activeTab="updateActiveTab" />
      <DataTable :profiles="profilesToShow" :heading="getActiveTabName" />
    </div>
  </main>
</template>

<script>
import PageHeader from '@/components/PageHeader.vue'
import Sidebar from '@/components/PageSidebar.vue'
import DataTable from '@/components/DataTable.vue'

export default {
  components: {
    Sidebar,
    PageHeader,
    DataTable,
  },
  data() {
    return {
      profiles: [],
      activeTab: 'all',
    }
  },
  mounted() {
    this.fetchProfiles()
  },
  computed: {
    profilesToShow() {
      if (this.activeTab === 'all') {
        return this.profiles
      } else if (this.activeTab === 'processed') {
        return this.profiles.filter((profile) => profile.status)
      } else if (this.activeTab === 'pending') {
        return this.profiles.filter((profile) => !profile.status)
      } else {
        return []
      }
    },
    getActiveTabName() {
      switch (this.activeTab) {
        case 'all':
          return 'Все'
        case 'processed':
          return 'Обработанные'
        case 'pending':
          return 'Не обработанные'
        default:
          return ''
      }
    },
  },
  methods: {
    updateActiveTab(tab) {
      this.activeTab = tab
    },
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
.main-container {
  display: flex;
}
</style>
