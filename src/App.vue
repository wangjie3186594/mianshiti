<template>
  <div id="app">
    <!-- 标题 -->
    <button v-for="(item, index) in title" :key="index" @click="onSwitch(item.id)">{{item.name}}</button>
    <!-- 搜索框 -->
    <input type="text" placeholder="搜索" v-model="Searchkey" />
    <!-- 列表 -->
    <ul :class="{ list : isActive === 1 }">
      <li v-for="(item, index) in search(Searchkey)" :key="index">{{item.lists}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isActive: "", // 样式索引
      Searchkey: "", // 搜索关键词
      //  标题
      title: [
        { id: 0, name: "列表视图" },
        { id: 1, name: "网络视图" }
      ],
      // 列表数据
      list: [
        { id: 0, lists: "test1.txt" },
        { id: 1, lists: "test2.txt" },
        { id: 2, lists: "test3.txt" },
        { id: 3, lists: "test4.txt" },
        { id: 4, lists: "testtest5.txt" }
      ]
    };
  },
  methods: {
    // 实现切换功能
    onSwitch(id) {
      if (id === 1) {
        this.isActive = id;
      } else {
        this.isActive = 0;
      }
    },
    // 搜索功能
    search(Searchkey) {
      return this.list.filter(item => {
        if (item.lists.includes(Searchkey)) {
          return item;
        }
      });
    }
  }
};
</script>

<style lang="less" scoped>
.list {
  display: flex;
  width: 100%;
  li {
    width: 200px;
    height: 200px;
    border: 1px solid black;
  }
}
</style>
