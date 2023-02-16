<template>
  <div class="tickers">
    <div class="tickers-head">
        <div class="tickers-title">
            <h1>Bekijk {{type}}</h1>
            <p>
               Bekijk het rendement vanaf
                {{date.getDate() < 10 ? `0${date.getDate()}` : date.getDate()}}-{{months[date.getMonth()]}}-{{date.getFullYear() - 5}}
            </p>
        </div>
        <div class="tickers-settings">
            <div>
                Startbedrag in € <input type="text" v-model="startingAmount">
            </div>
            <div>
                Maandelijkse inleg in € <input type="text" v-model="monthlyAmount">
            </div>
        </div>
    </div>
    <div class="tickers-data">
        <Card 
            v-for="item in tickers"
            v-bind:key="item"
            :stock="item"
            :startingAmount="startingAmount"
            :monthlyAmount="monthlyAmount"
        />
    </div>
  </div>
</template>

<script>
import Card from './Card.vue';

export default {
    name: "Cards",
    data() {
        return {
            startingAmount: 1000,
            monthlyAmount: 100,
            date: new Date(),
            months: ["01", "02", "03", "04", "05", "06","07", "08", "09", "10", "11", "12"]
        }
    },
    props: {
        tickers: JSON, type: String
    },
    components: {
        Card
    }
}
</script>

<style lang="scss" scoped>
    .tickers {
        .tickers-head {
            padding: 30px 0px;
            .tickers-title {
                margin-bottom: 10px;
                h1 {
                    font-weight: 500;
                }
                p {
                    color: #5f676e;
                }
            }
            .tickers-settings {
                div {
                    input {
                        border: none;
                        background-color: #f9fafb;
                    }
                }
            }
        }
    }

    @media only screen and (max-width: 900px) {
        .tickers {
            padding: 0 4vw;
            .tickers-data {
                margin: 0 auto;
                display: flex;
                gap: 20px;
                flex-wrap: wrap;
            }
        }
    }

    @media only screen and (min-width: 820px) and (max-width: 1440px) {
        .tickers {
            padding: 0 2vw;
            .tickers-data {
                margin: 0 auto;
                display: flex;
                gap: 20px;
                flex-wrap: wrap;
            }
        }   
    }

    @media only screen and (min-width: 1440px) {
        .tickers {
            padding: 0 1vw;
            .tickers-data {
                margin: 0 auto;
                display: flex;
                gap: 20px;
                flex-wrap: wrap;
            }
        }
    }
</style>