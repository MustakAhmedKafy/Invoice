<script setup>
const invoiceLogo = "/invoice.jpg";
</script>
<template>
  <section class="invoice bg-light py-5">
    <div class="container bg-white rounded">
      <div class="row">
        <div class="col-md-9">
          <img :src="invoiceLogo" alt="" />
          <div class="row">
            <div class="col-md-5">
              <input
                type="text"
                class="form-control mb-3"
                placeholder="who is invoice from? (required)"
              />
            </div>
          </div>
          <div class="row">
            <div class="col-md-5 mb-3">
              <label for="">Bill to</label>
              <input
                type="text"
                class="form-control"
                placeholder="who is invoice to? (required)"
              />
            </div>
            <div class="col-md-5">
              <input
                type="text"
                class="form-control mt-4"
                placeholder="Optional"
              />
            </div>
          </div>
        </div>
        <div class="col-md-3">
          <h1>Invoice</h1>
          <div class="input-group mb-3">
            <span class="input-group-text" id="basic-addon1">#</span>
            <input
              type="text"
              class="form-control"
              aria-describedby="basic-addon1"
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
              class="form-control rounded"
              aria-describedby="basic-addon1"
            />
          </div>
          <div class="input-group mb-3">
            <span
              class="input-group-text bg-transparent border-0"
              id="basic-addon1"
              >Payment Terms</span
            >
            <input
              type="text"
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
              type="date"
              class="form-control rounded"
              aria-describedby="basic-addon1"
            />
          </div>
          <div class="input-group mb-3">
            <span
              class="input-group-text bg-transparent border-0"
              id="basic-addon1"
              >PO Number</span
            >
            <input
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
            <td>
              <input
                type="text"
                class="form-control"
                aria-describedby="basic-addon1"
              />
            </td>
          </tr>
        </tbody>
      </table>
      <button class="btn btn-success ms-2">+ Line Add</button>

      <div class="row">
        <div class="col-md-8">
          <div class="terms mt-5">
            <label for="">Notes</label>
            <textarea
              name="message"
              class="form-control w-75 mb-3"
              rows="2"
              placeholder="Notes - any relevant information not already covered"
              data-v-00bf26c8=""
            ></textarea>
            <label for="">Terms</label>
            <textarea
              name="message"
              class="form-control w-75 mb-3"
              rows="2"
              placeholder="Terms and conditions - late fees, payment methods, delivery schedule"
              data-v-00bf26c8=""
            ></textarea>
          </div>
        </div>
        <div class="col-md-4">
          <table class="table sub-total">
            <tbody>
              <tr>
                <th scope="col">Sub Total</th>
                <td>$0.00</td>
              </tr>

              <tr>
                <th scope="col">Tax</th>
                <td>
                  <input
                    type="text"
                    class="form-control"
                    aria-describedby="basic-addon1"
                    value="0%"
                  />
                </td>
              </tr>

              <tr>
                <th scope="col"></th>
                <td>
                  <a href="" class="me-4">+Discount </a>
                  <a href="">+Shipping </a>
                </td>
              </tr>

              <tr>
                <th scope="col">Total</th>
                <td>$0.00</td>
              </tr>

              <tr>
                <th scope="col">Amount Paid</th>
                <td>
                  <input
                    type="text"
                    class="form-control"
                    aria-describedby="basic-addon1"
                    value="0%"
                  />
                </td>
              </tr>

              <tr>
                <th scope="col">Sub Total</th>
                <td>$0.00</td>
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
 tr, td, th {
  border: 0px;
}

.form-control {
  box-shadow: none;
}
input:focus, textarea:focus {
  border: 1px solid green;
}
</style>
