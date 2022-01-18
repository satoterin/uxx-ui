<template>
  <div class="dapp">
    <div class="container">
      <div class="first-box">
        <div
          class="home-header"
          id="metrics;"
        >
          <div>
            <span class="circulating">Circulating UXX</span
            ><span v-text="stats.circulating"></span>
          </div>
          <div>
            <span class="header-title">Staked</span
            ><span v-text="stats.staked"></span>
          </div>
          <div>
            <span class="header-title">Mining</span
            ><span v-text="stats.mining"></span>
          </div>
          <div>
            <span class="header-title">Duration</span
            ><span v-text="stats.duration"></span>
          </div>
          <div>
            <span class="header-title">Yield</span
            ><span v-text="stats.yield"></span>
          </div>
          <div></div>
        </div>
        <div class="yield-box">
          <div class="title">yield Curve</div>
          <div>
            <div class="range-header d-flex justify-content-between px-4 py-1">
              <span class="me-3">INFLATION</span><span class="range-output">{{inflationValue}}%</span>
              <div class="range-slider bg-ruler">
                <b-form-input id="inflation-range myRange" class="slider" v-model="inflationValue" type="range" min="0" max="100"></b-form-input>
              </div>
              <span class="text-primary d-flex align-content-center justify-content-center" style="color: #6d1eda!important;">STAKING</span>
            </div>
          </div>
          
          <line-chart></line-chart>
        </div>
        <div class="stake-box">
          <div class="title">my Stakes</div>
          <div class="stake-content">
            <table class="stake-table">
              <tbody>
                <tr style="border-bottom:1px solid #707070; margin-bottom: 5px; height: 25px">
                  <th>Contracts</th>
                  <th>Maturity</th>
                  <th>Time(Years)</th>
                  <th>UXX</th>
                  <th>Yield</th>
                  <th>Exit Fee %</th>
                  <th>Exit Fee UXX</th>
                </tr>
                <tr>
                  <td>MARCH25</td>
                  <td>30-Mar-25</td>
                  <td>3.50</td>
                  <td>100,000</td>
                  <td>12.90%</td>
                  <td>-30.51%</td>
                  <td>(30,510)</td>
                </tr>
                <tr>
                  <td>MARCH25</td>
                  <td>30-Mar-25</td>
                  <td>3.50</td>
                  <td>100,000</td>
                  <td>12.90%</td>
                  <td>-30.51%</td>
                  <td>(30,510)</td>
                </tr>
                <tr>
                  <td>MARCH25</td>
                  <td>30-Mar-25</td>
                  <td>3.50</td>
                  <td>100,000</td>
                  <td>12.90%</td>
                  <td>-30.51%</td>
                  <td>(30,510)</td>
                </tr>
                <tr>
                  <td>MARCH25</td>
                  <td>30-Mar-25</td>
                  <td>3.50</td>
                  <td>100,000</td>
                  <td>12.90%</td>
                  <td>-30.51%</td>
                  <td>(30,510)</td>
                </tr>
                <tr>
                  <td>MARCH25</td>
                  <td>30-Mar-25</td>
                  <td>3.50</td>
                  <td>100,000</td>
                  <td>12.90%</td>
                  <td>-30.51%</td>
                  <td>(30,510)</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
      <div class="liquidity-box">
        <div class="box">
          <div class="title">liquidity</div>
          <div>
            <table class="uxxTable">
              <tbody>
                <tr>
                  <td class="lab1">Liquid</td>
                  <td class="lab2">15,000,000</td>
                  <td></td>
                </tr>
                <tr>
                  <td class="lab1">Inflation</td>
                  <td class="lab2">225,000</td>
                  <td><button class="btn">Claim</button></td>
                </tr>
                <tr>
                  <td class="lab1">Mining</td>
                  <td class="lab2">1,000,000</td>
                  <td><button class="btn">Claim</button></td>
                </tr>
                <tr>
                  <td class="lab3">Unstaked</td>
                  <td class="lab4">133,000</td>
                  <td></td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
        <div class="order-box">
          <div class="title">order Entry</div>
          <div>
            <div class="order-header">
              <span class="title-single">Single</span>
              <toggle-button :value="true"
               color="#D4B5FF"
               :sync="true"
               :labels="true"
               class="toggle"/>
               <span class="title-single">Multi</span
              >
            </div>
            <hr style="margin-top: 8px"/>
            <table class="order-table">
              <tbody>
                <tr>
                  <td>Maturity</td>
                  <div>
                    <td><button class="table-btn1">*Month</button></td>
                    <td><button class="table-btn2">*Year</button></td>
                  </div>
                </tr>
                <tr>
                  <td>Date</td>
                  <div>
                    <td><button class="table-btn1">19/12/2025</button></td>
                    <td><button class="table-btn2">4.23</button></td>
                  </div>
                </tr>
                <tr>
                  <td>Open Interest</td>
                  <div>
                    <td><button class="table-btn1">600,000</button></td>
                    <td><button class="table-btn2">1.5%</button></td>
                  </div>
                </tr>
                <tr>
                  <td>Daily Delta</td>
                  <div>
                    <td><button class="table-btn1">(5,000)</button></td>
                    <td><button class="table-btn2">0.135%</button></td>
                  </div>
                </tr>
                <tr>
                  <td>Yield / Exit Fee</td>
                  <div>
                    <td><button class="table-btn1">14.61%</button></td>
                    <td><button class="table-btn2">34.65%</button></td>
                  </div>
                </tr>
                <tr>
                  <td>Position</td>
                  <div>
                    <td><button class="table-btn1">20,000</button></td>
                    <td><button class="table-btn2">0.0500%</button></td>
                  </div>
                </tr>
                <tr>
                  <td>Quantity</td>
                  <div>
                    <td><button class="table-btn1">*Quantity</button></td>
                    <td><button class="table-btn2">0.0025%</button></td>
                  </div>
                </tr>
              </tbody>
            </table>
            <div class="btn-group">
              <button class="stake-btn">Stake</button>
              <button class="withdraw-btn">Withdraw</button>
            </div>
          </div>
        </div>
        <div class="recent-box">
          <div class="title">recent Transactions</div>
          <div class="recent">
            <table class="recent-table">
              <tbody>
                <tr style="border-bottom: 1px solid #707070; height: 23px">
                  <th>Time</th>
                  <th>Account</th>
                  <th>Action</th>
                  <th>UXX Gross</th>
                  <th>Maturity</th>
                </tr>
                <tr>
                  <td>09:25</td>
                  <td>genesis1…</td>
                  <td>STAKE</td>
                  <td>100,000</td>
                  <td>DEC26</td>
                </tr>
                <tr>
                  <td>09:25</td>
                  <td>genesis1…</td>
                  <td>STAKE</td>
                  <td>100,000</td>
                  <td>DEC26</td>
                </tr>
                <tr>
                  <td>09:25</td>
                  <td>genesis1…</td>
                  <td>STAKE</td>
                  <td>100,000</td>
                  <td>DEC26</td>
                </tr>
                <tr>
                  <td>09:25</td>
                  <td>genesis1…</td>
                  <td>STAKE</td>
                  <td>100,000</td>
                  <td>DEC26</td>
                </tr>
                <tr>
                  <td>09:25</td>
                  <td>genesis1…</td>
                  <td>STAKE</td>
                  <td>100,000</td>
                  <td>DEC26</td>
                </tr>
                <tr>
                  <td>09:25</td>
                  <td>genesis1…</td>
                  <td>STAKE</td>
                  <td>100,000</td>
                  <td>DEC26</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Chart from "./Chart.vue"
import LineChart from './LineChart'
export default {
  data() {
    return {
      inflationValue: 2.7,
      orderType: "Single",
      stats: {
        circulating: "40,000,000",
        staked: "24,000,000",
        mining: "33%",
        duration: 5.125,
        yield: "16.61%",
      },
      initialGraphData: [
        {
          t: 0.5,
          st: 2.5,
          ytstake: 13.13,
          ryt: -0.07,
        },
        {
          t: 1,
          st: 2.5,
          ytstake: 14.03,
          ryt: 0.82,
        },
        {
          t: 1.5,
          st: 2.5,
          ytstake: 14.98,
          ryt: 1.78,
        },
        {
          t: 2,
          st: 2.5,
          ytstake: 16.01,
          ryt: 2.8,
        },
        {
          t: 2.5,
          st: 2.5,
          ytstake: 17.1,
          ryt: 3.9,
        },
        {
          t: 3,
          st: 2.5,
          ytstake: 18.27,
          ryt: 5.06,
        },
        {
          t: 3.5,
          st: 2.5,
          ytstake: 19.51,
          ryt: 6.31,
        },
        {
          t: 4,
          st: 2.5,
          ytstake: 20.85,
          ryt: 7.64,
        },
        {
          t: 4.5,
          st: 2.5,
          ytstake: 22.27,
          ryt: 9.06,
        },
        {
          t: 5,
          st: 2.5,
          ytstake: 23.79,
          ryt: 10.58,
        },
        {
          t: 5.5,
          st: 2.5,
          ytstake: 25.41,
          ryt: 12.21,
        },
        {
          t: 6,
          st: 2.5,
          ytstake: 27.14,
          ryt: 13.94,
        },
        {
          t: 6.5,
          st: 2.5,
          ytstake: 29,
          ryt: 15.79,
        },
        {
          t: 7,
          st: 2.5,
          ytstake: 30.98,
          ryt: 17.77,
        },
        {
          t: 7.5,
          st: 2.5,
          ytstake: 33.09,
          ryt: 19.89,
        },
        {
          t: 8,
          st: 2.5,
          ytstake: 33.35,
          ryt: 22.14,
        },
        {
          t: 8.5,
          st: 2.5,
          ytstake: 37.76,
          ryt: 24.56,
        },
        {
          t: 9,
          st: 2.5,
          ytstake: 40.34,
          ryt: 27.13,
        },
        {
          t: 9.5,
          st: 2.5,
          ytstake: 43.09,
          ryt: 29.89,
        },
        {
          t: 10,
          st: 2.5,
          ytstake: 46.03,
          ryt: 32.83,
        },
      ],
    };
  },
  computed: {
    graphData() {},
  },
  components: {
    LineChart
  }
};
</script>