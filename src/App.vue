<template>
  <div id="app">
    <table>
      <thead>
        <tr>
          <th scope="col">品項</th>
          <th scope="col">描述</th>
          <th scope="col">價格</th>
          <th scope="col">庫存</th>
          <th scope="col">操作</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in menuItems" :key="index">
          <td>
            <input v-if="item.editingName" v-model="item.name" @blur="item.editingName = false" @keyup.enter="item.editingName = false">
            <span v-else @click="item.editingName = true">{{ item.name }}</span>
          </td>
          <td>{{ item.description }}</td>
          <td>{{ item.price }}</td>
          <td>
            <button @click="decreaseStock(index)">-</button>
            {{ item.stock }}
            <button @click="increaseStock(index)">+</button>
          </td>
          <td>
            <button @click="editName(index)">編輯名稱</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      menuItems: [
        { name: '珍珠奶茶', description: '香濃奶茶搭配QQ珍珠', price: 50, stock: 20, editingName: false },
        { name: '冬瓜檸檬', description: '清新冬瓜配上新鮮檸檬', price: 45, stock: 18, editingName: false },
        { name: '翡翠檸檬', description: '綠茶與檸檬的完美結合', price: 55, stock: 34, editingName: false },
        { name: '四季春茶', description: '香醇四季春茶，回甘無比', price: 45, stock: 10, editingName: false },
        { name: '阿薩姆奶茶', description: '阿薩姆紅茶搭配香醇鮮奶', price: 50, stock: 25, editingName: false },
        { name: '檸檬冰茶', description: '檸檬與冰茶的清新組合', price: 45, stock: 20, editingName: false },
        { name: '芒果綠茶', description: '芒果與綠茶的獨特風味', price: 55, stock: 18, editingName: false },
        { name: '抹茶拿鐵', description: '抹茶與鮮奶的絕配', price: 60, stock: 20, editingName: false }
      ]
    };
  },
  methods: {
    decreaseStock(index) {
      if (this.menuItems[index].stock > 0) {
        this.menuItems[index].stock--;
      }
    },
    increaseStock(index) {
      this.menuItems[index].stock++;
    },
    editName(index) {
      this.menuItems[index].editingName = true;
    }
  }
};
</script>

<style>
table {
  width: 100%;
  border-collapse: collapse;
}
th, td {
  border: 1px solid #ddd;
  padding: 8px;
}
th {
  background-color: #f4f4f4;
}
td input {
  width: 100%;
  box-sizing: border-box;
}
</style>
