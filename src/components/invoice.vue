<script setup>
import { reactive } from "vue";
const invoiceLogo = "/invoice.jpg";

const data = reactive({
  sender: "",
  billTo: "",
  shipTo: "",
  invoiceNumber: "",
  date: "",
  dueDate: "",
  additionalNote: "",
  items: [
    {
      description: "",
      quantity: "",
      rate: "",
      amount: "",
    },
  ],
  items: [
    {
      description: "",
      quantity: "",
      rate: "",
      amount: "",
    },
  ],
  notes: "",
  terms: "",
  subtotal: "",
  tax: "",
  total: "",
});

// add more item
function addMoreItem() {
  data.items.push({
    description: "",
    quantity: "",
    rate: "",
    amount: "",
  });
}

// subtotal
function getSubTotal() {
  let subtotal = 0;
  data.items.forEach((item) => {
    subtotal += item.amount;
  });
  data.subtotal = subtotal;
  return subtotal;
}
// Total
function getTotal() {
  const tax = (data.subtotal * data.tax) / 100;
  data.total = data.subtotal + tax;
  return data.total; // Return data.total instead of total
}
</script>
<template>
  <section class="invoice bg-light py-5">
    <div class="container bg-white rounded">
      <div class="row">
        <div class="col-md-9">
          <img :src="invoiceLogo" alt="" />
          <div class="row">
            <div class="col-md-5">
              <Label>Sender</Label>
              <input
                v-model="data.sender"
                type="text"
                class="form-control mb-3"
              />
            </div>
          </div>
          <div class="row">
            <div class="col-md-5 mb-3">
              <label for="">Bill to</label>
              <input v-model="data.billTo" type="text" class="form-control" />
            </div>
            <div class="col-md-5">
              <label for="">Ship to</label>
              <input v-model="data.shipTo" type="text" class="form-control" />
            </div>
          </div>
        </div>
        <div class="col-md-3">
          <h1>Invoice</h1>
          <div class="mb-3">
            <input
              v-model="data.invoiceNumber"
              type="text"
              class="form-control"
            />
          </div>
          <div class="input-group mb-3">
            <span
              class="input-group-text bg-transparent border-0"
              id="basic-addon1"
              >Date</span
            >
            <input
              type="date"
              v-model="data.date"
              class="form-control rounded"
              aria-describedby="basic-addon1"
            />
          </div>

          <div class="input-group mb-3">
            <span
              class="input-group-text bg-transparent border-0"
              id="basic-addon1"
              >Due Date</span
            >
            <input
              v-model="data.dueDate"
              type="date"
              class="form-control rounded"
              aria-describedby="basic-addon1"
            />
          </div>
          <div class="input-group mb-3">
            <span
              class="input-group-text bg-transparent border-0"
              id="basic-addon1"
              >Additional Note</span
            >
            <input
              v-model="data.additionalNote"
              type="text"
              class="form-control rounded"
              aria-describedby="basic-addon1"
            />
          </div>
        </div>
      </div>

      <!-- items table -->
      <table class="table">
        <thead>
          <tr class="bg-light">
            <th>Item</th>
            <th>Quality</th>
            <th>Rate</th>
            <th>Amount</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in data.items" :key="index">
            <td>
              <input
                v-model="item.description"
                type="text"
                class="form-control"
                aria-describedby="basic-addon1"
                placeholder="Description of services or product..."
              />
            </td>
            <td>
              <input
                v-model="item.quantity"
                type="number"
                class="form-control"
                aria-describedby="basic-addon1"
              />
            </td>
            <td>
              <input
                v-model="item.rate"
                type="number"
                class="form-control"
                aria-describedby="basic-addon1"
              />
            </td>
            <td>${{ (item.amount = item.quantity * item.rate) }}</td>
          </tr>
        </tbody>
      </table>
      <button @click="addMoreItem()" class="btn btn-success ms-2">
        + Line Add
      </button>

      <div class="py-5">
        <p>{{ data }}</p>
      </div>

      <div class="row">
        <div class="col-md-8">
          <div class="terms mt-5">
            <label for="">Notes</label>
            <textarea
              v-model="data.notes"
              name="message"
              class="form-control w-75 mb-3"
              rows="2"
            ></textarea>
            <label for="">Terms</label>
            <textarea
              v-model="data.terms"
              name="message"
              class="form-control w-75 mb-3"
              rows="2"
            ></textarea>
          </div>
        </div>

        <!-- subtotal -->
        <div class="col-md-4">
          <table class="table sub-total">
            <tbody>
              <tr>
                <th scope="col">SubTotal</th>
                <td>
                  <input
                    type="number"
                    :value="getSubTotal()"
                    readonly
                    class="form-control"
                    aria-describedby="basic-addon1"
                    placeholder="SubTotal"
                  />
                </td>
              </tr>
              <tr>
                <th scope="col">Tax</th>
                <td>
                  <input
                    v-model="data.tax"
                    type="number"
                    class="form-control"
                    aria-describedby="basic-addon1"
                    value="0%"
                  />
                </td>
              </tr>
              <tr>
                <th scope="col">Total</th>
                <td>
                  <input
                    :value="getTotal()"
                    type="number"
                    readonly
                    class="form-control"
                    aria-describedby="basic-addon1"
                    placeholder="Total"
                  />
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
a {
  text-decoration: none;
}
img {
  width: 150px;
}
.table.sub-total tr {
  text-align: end;
}
.table.sub-total input {
  text-align: end;
}
tr,
td,
th {
  border: 0px;
}

.form-control {
  box-shadow: none;
}
input:focus,
textarea:focus {
  border: 1px solid green;
}
</style>
