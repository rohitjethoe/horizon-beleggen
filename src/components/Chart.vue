<template>
  <div class="ticker">
    <div class="ticker-details">
      <div class="ticker-data ticker-logo">
        <img :src="stock.logo" alt="">
      </div>
      <div class="ticker-data ticker-name">
        {{stock.name}}
      </div>
      <div class="ticker-data ticker-value">
        €{{stock.data[0].close.toFixed(2)}}
      </div>
    </div>
    <div class="ticker-data ticker-invest-value">
      <span>Investering:</span> €{{investValue.toFixed(0)}}
    </div>
    <div class="ticker-data ticker-investment-value">
      <span>Portfolio waarde:</span> €{{(shares * stock.data[0].close).toFixed(2)}}
    </div>
    <div 
      class="ticker-profit" 
      :class="profit > 0 ? 'ticker-profit-positive' : 'ticker-profit-negative'"
    >
      {{profit.toFixed(2)}}%
    </div>
  </div>
</template>

<script>
export default {
    name: "Chart",
    data() {
      return {
        profit: 0, 
        shares: this.startValue / this.stock.data[Object.keys(this.stock.data).length - 1].close,
        investValue: 0,
        startValue: 1000,
        monthlyValue: 100
      }
    },
    props: {
        stock: JSON, startingAmount: {
          type: null,
          default: 1000
        },
        monthlyAmount: {
          type: null,
          default: 100
        }
    },
    methods: {
      calculateData: function () {
        this.shares = this.startValue / this.stock.data[Object.keys(this.stock.data).length - 1].close;
        for (let i = 1; i < Object.keys(this.stock.data).length; i++) {
          this.investValue = this.startValue + (this.monthlyValue * Object.keys(this.stock.data).length)
          this.shares += this.monthlyValue / this.stock.data[Object.keys(this.stock.data).length - (i + 1)].close;
          this.profit = ((this.shares * this.stock.data[0].close) - this.investValue) / this.investValue * 100
        }
      }
    },
    created() {
      this.calculateData(this.startingAmount, this.monthlyAmount);
    },
    watch: {
      startingAmount: function (newStartingAmount, oldStartingAmount) {
        this.startValue = parseInt(newStartingAmount);
        this.calculateData();
      },
      monthlyAmount: function (newMonthlyAmount, oldMonthlyAmount) {
        this.monthlyValue = parseInt(newMonthlyAmount);
        this.calculateData();
      }
    }
}
</script>

<style lang="scss" scoped>
  .ticker {
    background-color: #fff;
    color: #27332f;
    width: 300px;
    padding: 20px 30px;
    padding-bottom: 30px;
    border-radius: 12px;
    box-shadow: rgba(149, 157, 165, 0.2) 0px 6px 18px;
    .ticker-details {
      margin: 10px 0px;
      .ticker-name {
        font-weight: 600;
        font-size: 18px;
      }
      .ticker-logo {
        img {
          width: 40px;
          height: 40px;
        }
      }
    }
    .ticker-data {
      font-weight: 400;
      margin: 2px 0px;
      span {
        font-weight: 600;
      }
    }
    .ticker-profit {
      margin: 10px 0px;
      font-size: 20px;
    }
    .ticker-profit-positive {
      color: #04aa6d;
    }
    .ticker-profit-negative {
      color: #9a0e0e;
    }
  }
  @media only screen and (max-width: 820px) {
    .ticker {
      width: 260px;
      margin: 20px 0px;
      margin-right: 10px;
    }
  }

  @media only screen and (max-width: 700px) {
    .ticker {
      width: 60vw;
      margin: 0px 0px;
    }
  }

  @media only screen and (min-width: 820px) and (max-width: 1440px) {
    .ticker {
      width: 250px;    
    }
  }

  @media only screen and (min-width: 1440px) {
    .ticker {
      width: 360px;
    }
  }
</style>