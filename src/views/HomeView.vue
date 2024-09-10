<script setup>
import { ref } from 'vue';

const accountBalance = ref(400)

const transactions = ref([
  { id: "xy8723ougihk8o7ii", name: "Alex", amount: 10 },
  { id: "ww9732ougihk8wdvk", name: "Richard", amount: -10 },
  { id: "xy8723ougihk8o7ii", name: "Alex", amount: 10 },
]);
</script>

<template>
  <main>
    <div class="dashboard-container">
      <header class="dashboard-header">
        <h1 class="logo">SpendCryptAI</h1>
        <p class="tagline">Spend and monitor your assets in real time</p>
      </header>
      <div class="line">
      </div>
      <br>
      <br>

      <div class="innerwidth">
        <section class="assets-section">
          <div class="total-assets">
            <div class="assets-info">
              <h2>Total Assets</h2>
              <div class="coinflex">
                <div>
                  <img src="https://res.cloudinary.com/dnuhjsckk/image/upload/v1721718651/coinn_apt0iv.png"
                    class="coin-icon">
                </div>
                <div>
                  <p class="assets-amount">$151,000.00</p>
                </div>
              </div>
            </div>
          </div>
          <div class="income-expenditure">
            <div class="income">
              <h3> Balance: </h3>
              <p class="income-amount">
                <span :style="accountBalance > 0 ? 'color: #00ff00' : 'color: #ff0000'"> ${{ accountBalance }} </span>
              </p>
            </div>
          </div>
        </section>
        <br>

        <section class="realtime-tracker">
          <h2>Transaction History</h2>
          <div v-for="transaction in transactions" :key="transaction.id">
            <!-- <div :class="transaction.amount > 0 ? 'tracker-item transfer' : 'tracker-item receive'"> -->
            <div class="tracker-item"
              :style="transaction.amount > 0 ? 'border-left: 4px solid #00ff00' : 'border-left: 4px solid #ff0000'">
              <p>{{ transaction.amount > 0 ? 'Account Credited from ' : 'Account Debited for ' }} {{ transaction.id }}
              </p>
            </div>
          </div>

        </section>
      </div>
    </div>
  </main>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "IBM Plex Sans Thai", sans-serif;
}

main {
  margin: 0;
  padding: 0;
  background-color: #1E1F24;
  color: #ffffff;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.dashboard-container {
  width: 90%;
  max-width: 1200px;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.dashboard-header {
  text-align: center;
  margin-bottom: 30px;
}

.logo {
  Font-weight: 700;
  Font-family: poppins;
  font-size: 35px;
  color: #E2E0E0;
  letter-spacing: -2px;
}

.line {
  background: rgba(50, 58, 74, 0.5);
  padding: 1px;
}


.tagline {
  font-size: 17px;
  color: #999999;
  margin-top: -5px;
  font-weight: 300;
}

.assets-section {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 30px;
}

.total-assets {
  display: flex;
  align-items: center;
}

.coin-icon {
  width: 60px;
  height: 60px;
  margin-right: 20px;
}

.coinflex {
  display: flex;
  align-items: center;
}

.assets-info h2 {
  font-size: 16px;
  font-weight: 400;
  margin-bottom: 10px;
  color: rgb(241, 240, 240, 0.8);
}

.assets-amount {
  font-weight: 700;
  font-family: 'Poppins';
  font-size: 25px;
  color: rgb(241, 240, 240);
}

.income-expenditure {
  display: flex;
  gap: 20px;
}

.income,
.expenditure {
  background-color: #292A2F;
  padding: 10px 40px;
  border-radius: 15px;
  text-align: center;
}

.income h3,
.expenditure h3 {
  margin-bottom: -3px;
  font-weight: 400;
  font-size: 17px;
}

.income-amount {
  font-weight: 600;
  font-size: 28px;
  font-family: poppins;
  color: #35C93B;
}

.expenditure-amount {
  font-weight: 600;
  font-size: 28px;
  font-family: poppins;
  color: #FF3232;
}

.realtime-tracker {
  margin-top: 20px;
}

.realtime-tracker h2 {
  font-size: 18px;
  font-weight: 400;
  margin-bottom: 10px;
  color: rgb(241, 240, 240, 0.8);
}

.tracker-item {
  background-color: #3c3c3c;
  padding: 15px;
  border-radius: 8px;
  margin-bottom: 10px;
  display: flex;
  align-items: center;
}

.tracker-item.transfer {
  border-left: 4px solid #ff0000;
}

.tracker-item.receive {
  border-left: 4px solid #00ff00;
}

.tracker-item p {
  margin-left: 10px;
  color: #ffffff;
}

.innerwidth {
  margin: auto;
  max-width: 1050px;
}



@media (max-width: 768px) {
  .assets-section {
    flex-direction: column;
    align-items: flex-start;
  }

  .income-expenditure {
    width: 100%;
    justify-content: space-around;
    margin-top: 20px;
  }

  .income,
  .expenditure {
    width: 45%;
  }
}
</style>
