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
  notes: "",
  terms: "",
  subtotal: "",
  tax: "",
  total: "",
});
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
              <input v-model="data.sender" type="text" class="form-control mb-3" />
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
              <input v-model="data.invoiceNumber" type="text" class="form-control">
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
          <tr>
            <td>
              <input
                type="text"
                class="form-control"
                aria-describedby="basic-addon1"
                placeholder="Description of services or product..."
              />
            </td>
            <td>
              <input
                type="text"
                class="form-control"
                aria-describedby="basic-addon1"
              />
            </td>
            <td>
              <input
                type="text"
                class="form-control"
                aria-describedby="basic-addon1"
              />
            </td>
            <td>$0.00</td>
          </tr>
        </tbody>
      </table>
      <button class="btn btn-success ms-2">+ Line Add</button>

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
        <div class="col-md-4">
          <table class="table sub-total">
            <tbody>
              <tr>
                <th scope="col">SubTotal</th>
                <td>
                  <input
                    type="text"
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
                    type="text"
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
