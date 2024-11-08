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
}
</script>

<template>
  <header>
    <PageHeader />
  </header>
  <main>
    <div class="main-container">
      <Sidebar />
      <DataTable />
    </div>
  </main>
</template>

<style scoped>
.main-container {
  display: flex;
}
</style>
