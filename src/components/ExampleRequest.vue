<template>
  <div class="main">
    <button class="button" @click="getPrices">Make request</button>
    <textarea class="request-area" :value="requestData"></textarea>
  </div>
</template>

<script>
export default {
  name: 'ExampleRequest',
  data() {
    return {
      requestData: 'Wait for the request to be made...',
      testToken: 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoiMTc5MzljZmMtOWZlOS00YWYyLTg2YTctMTk1Y2M4ZDY1ZmJmIiwiYXVkIjpbImZhc3RhcGktdXNlcnM6YXV0aCIsImZhc3RhcGktdXNlcnM6dmVyaWZ5IiwiZmFzdGFwaS11c2Vyczp2ZXJpZnkiLCJmYXN0YXBpLXVzZXJzOnZlcmlmeSIsImZhc3RhcGktdXNlcnM6dmVyaWZ5Il19.zO7XWDtfte1ljqJnPdu-x-QjRHdx0oz26F-5zF2KRgI'
    }
  },
  methods: {
    async makeRequest(url, params, options) {
      url += '?' + (new URLSearchParams(params)).toString();
      return fetch(url, options);
    },
    async getPrices() {
      const response = await this.makeRequest(
        'https://api.quantor.me/v1/eth/contract/erc20/prices/time_range',
        {
          contract_address: '0xe3411d7ba6e99d4228e304ed1bbb4dff14813070',
          limit: 10000,
          after: 1,
          before: 1658766198820,
          granularity: 'day'
        },
        {
          method: 'POST',
          headers: { authorization: `Bearer ${this.testToken}` }
        }
      );
      this.requestData = JSON.stringify(await response.json(), null, 2);
    }
  },
}
</script>

<style scoped>
.main {
  margin: 0 auto;
  width: 50%;
}

@media only screen and (max-width: 768px) {
  .main {
    width: 100%;
  }
}

.request-area {
  width: calc(100% - 42px);
  height: 200px;
  padding: 20px;
  border: 1px solid #ccc;
}

.button {
  margin-top: 20px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #fff;
  color: #2c3e50;
  cursor: pointer;
  margin-bottom: 40px;
}
</style>
