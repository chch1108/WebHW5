<template>
  <div>
    <div class="form-row">
      <div class="form-group col-md-4">
        <label for="year">Year</label>
        <input type="number" id="year" name="year" class="form-control" v-model="year">
      </div>
      <div class="form-group col-md-4">
        <label for="month">Month</label>
        <input type="number" id="month" name="month" class="form-control" v-model="month">
      </div>
      <div class="form-group col-md-4">
        <label for="price">Price</label>
        <input type="number" step="0.01" id="price" name="price" class="form-control" v-model="price">
      </div>
    </div>
    <button type="submit" class="btn btn-primary" style="height: 50px; width: 100px; background-color: #F08080; color: #000000; border-radius: 20px;" @click="insertData">Insert</button>
  </div>

  <!-- 外框的框線 -->
  <table id="table" style="border: 1px solid black; display: none;"></table>

  <div id="app" class="mt-5">
    <button v-on:click="showTable" class="btn btn-secondary btn-lg" style="height: 100px; width: 100px; background-color: #8FBC8F; color: #000000; border-radius: 50px;">Show Data</button>
    <table class="table table-hover mt-5" style="border: 1px solid black;" v-if="showTableFlag">
      <thead id="mytable">
      <tr>
        <th>Year</th>
        <th>Month</th>
        <th>Price</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="item in showData" :key="item.year + item.month + item.price">
        <td>{{ item.year }}</td>
        <td>{{ item.month }}</td>
        <td>{{ item.price }}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      year: null,
      month: null,
      price: null,
      showData: [
        { year: 2023, month: 5, price: 44.5 }
      ],
      showTableFlag: false
    }
  },
  methods: {
    insertData() {
      let item = {
        year: this.year,
        month: this.month,
        price: this.price
      }
      this.showData.push(item)
      this.year = null
      this.month = null
      this.price = null
    },
    showTable() {
      this.showTableFlag = true
    }
  }
};
</script>


<style scoped>
/* 修改表格的配色 */
table {
  background-color: #ffffff; /* 表格背景色 */
}
tr:nth-child(even) {
  background-color: #F0FFF0; /* 偶数行背景色 */
}
td {
  padding: 10px;
}
/* 修改表格的框线 */
table {
  border-collapse: collapse;
  border: 2px solid #000000;
}

#mytable {
  background-color: #8FBC8F;
  color: black;
}

</style>