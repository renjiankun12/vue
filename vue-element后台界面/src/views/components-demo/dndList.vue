<template>
<el-container>
  <el-aside width="50%">Aside</el-aside>
  <el-main>
    <div class="components-container">
    <div class="editor-container">
      <dnd-list :list1="list1" :list2="list2" list1Title="List" list2Title="Article pool"></dnd-list>
    </div>
  </div>
  </el-main>
</el-container>
</template>

<script>
import DndList from '@/components/DndList'
import { fetchList } from '@/api/article'

export default {
  name: 'dndList-demo',
  components: { DndList },
  data() {
    return {
      list1: [],
      list2: []
    }
  },
  created() {
    this.getData()
  },
  methods: {
    getData() {
      this.listLoading = true
      fetchList().then(response => {
        this.list1 = response.data.items.splice(0, 5)
        this.list2 = response.data.items
        console.log(response.data.items)
      })
    }
  }
}
</script>


