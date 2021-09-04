<template>
  <div>
    <div class="header flex gap-5">
      <div class="flex-1 bg-blue-200">
        <div>
          Invoice No
          <input type="text">
        </div>
        <div>
          Date
          <input type="date">
        </div>
      </div>
      <div class="flex-1 text-right bg-green-200">
        <div>Customer Name</div>
        <div><input type="text"></div>
      </div>
    </div>
    <div class="detail">
      
      <table class="w-full">
        <thead>
          <tr>
            <th class="text-center">Sr</th>
            <th class="text-left">Product Detail</th>
            <th class="text-center">Qty</th>
            <th class="text-center">Rate</th>
            <th class="text-center">Amount</th>
            <th>Actions</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item, i in items">
            <td class="text-center">{{i + 1}}</td>
            <td class="text-left"><input type="text" v-model="item.name"></td>
            <td class="text-center"><input type="text" v-model="item.qty"></td>
            <td class="text-center">&#8377; <input type="text" v-model="item.rate"></td>
            <td class="text-center">&#8377; {{ item.qty * item.rate }}</td>
            <td>
              <button class="rounded-full py-1 px-3 bg-gray-400 hover:bg-red-500 text-gray-200" @click="removeItem(i)">
                &times;
              </button>
            </td>
          </tr>
          <tr>
            <td>&nbsp;</td>
            <td><input ref="focusme" v-model="newItem.name" type="text"></td>
            <td><input v-model="newItem.qty" type="text"></td>
            <td>&#8377; <input v-model="newItem.rate" type="text" @keyup.enter="addItem()"></td>
            <td>&#8377; {{ newAmt }}</td>
          </tr>
        </tbody>
      </table> 

      <pre>{{newItem}}</pre>
    </div>
    <div class="footer">Footer</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newItem: {
        name: "",
        qty: 0,
        rate: 0
      },
      items: []
    }
  },
  methods: {
    resetNewItem() {
      this.newItem = {
        name: "", qty: 0, rate: 0
      };
    },
    addItem() {
      let item = Object.assign({}, this.newItem);
      this.items.push(item);
      this.resetNewItem();
      this.$refs.focusme.focus();
    },
    removeItem(i) {
      this.items.splice(i, 1)
    }
  },
  computed: {
    newAmt() {
      return Number(this.newItem.qty) * Number(this.newItem.rate)
    }
  }
}
</script>
