<template>
  <div class="box">
    <ul class="title_box">
      <li>购买盲盒</li>
      <li><img src="../../../assets/images/nftimage/nft_line_title.png" alt="" /></li>
      <li>购买盲盒参与游戏，自由交易</li>
    </ul>
    <div class="treasure_chest_box">
      <img src="../../../assets/images/nftimage/treasure_chest.png" alt="" />
    </div>
    <div class="buy_box">
      <div>
        <div class="title">The remaining /The total ：{{ proportion }}</div>
        <ul>
          <li>
            <div>价格</div>
            <div>{{ price }} ST</div>
          </li>
          <li>
            <div>数量</div>
            <div class="btns">
              <span class="btn" @click="deleteAmount">-</span>
              <input type="number" v-model="amount" />
              <span class="btn" @click="addAmount">+</span>
            </div>
          </li>
          <li>
            <div>总金额</div>
            <div>{{ totalAmount }} ST</div>
          </li>
        </ul>
        <div class="buy_btn" @click="clickBuy">购 买</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      proportion: "0/1500",
      price: 10,
      amount: 100,
      totalAmount: 10,
    };
  },
  watch: {
    amount(newVal, oldVal) {
      if (newVal && newVal <= 99999) {
        this.amount = newVal;
      } else {
        this.amount = oldVal;
        // console.log("");
      }
    },
  },
  methods: {
    clickBuy() {
      console.log("clickBuy", this.amount, typeof this.amount);
    },
    deleteAmount() {
      this.amount--;
    },
    addAmount() {
      this.amount++;
    },
  },
};
</script>

<style lang="scss" scoped>
.box {
  width: 100%;
  height: 90vh;
  background-image: url("../../../assets/images/nftimage/nft_bg4.png");
  background-size: 100% 100%;
  background-position: center center;
  position: relative;
  .title_box {
    margin: 0 auto;
    text-align: center;
    li {
      &:nth-child(1) {
        font-size: 45px;
        color: #00c1ff;
        line-height: 45px;
        background: linear-gradient(180deg, #825f35 0%, #fadd82 51%, #876333 100%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
      }
      &:nth-child(2) {
        img {
          width: 400px;
          height: auto;
          margin: 30px 0;
        }
      }
      &:nth-child(3) {
        font-size: 16px;
        color: #ffffff;
        line-height: 16px;
      }
    }
  }

  .buy_box {
    display: flex;
    justify-content: flex-end;
    > div {
      margin: 50px 0;
      padding: 50px 30px;
      background-image: url("../../../assets/images/nftimage/nft_bg5.png");
      background-size: 100% 100%;
      background-position: center center;
      .title {
        margin-bottom: 30px;
        font-size: 28px;
        color: #ffffff;
        line-height: 28px;
        background: linear-gradient(180deg, #825f35 0%, #fadd82 51%, #876333 100%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
      }
      ul {
        li {
          margin: 30px 0;
          display: flex;
          align-items: center;
          justify-content: space-between;
          div {
            &:nth-child(1) {
              font-size: 16px;
              color: #ffffff;
            }
            &:nth-child(2),
            input {
              font-size: 28px;
              color: #f1b713;
              background: linear-gradient(180deg, #825f35 0%, #fadd82 51%, #876333 100%);
              -webkit-background-clip: text;
              -webkit-text-fill-color: transparent;
            }
            &.btns {
              display: flex;
              align-items: center;
              span {
                display: flex;
                align-items: center;
                justify-content: center;
                cursor: pointer;
                width: 20px;
                height: 20px;
                border-radius: 50%;
                border: 1px solid #939393;
                font-size: 20px;
              }
              input {
                width: 3em;
                height: 100%;
                margin: 0 10px;
                text-align: right;
              }
            }
          }
        }
      }
      .buy_btn {
        width: fit-content;
        height: fit-content;
        margin: 0 auto;
        padding: 10px 80px;
        cursor: pointer;
        background: linear-gradient(180deg, #825f35 0%, #fadd82 51%, #876333 100%);
        box-shadow: inset 0px 2px 3px 0px #f2d383, inset 0px -2px 11px 0px #f2d57d;
        border-radius: 5px;
        font-size: 20px;
        color: #381a02;
        line-height: 20px;
      }
    }
  }
  .treasure_chest_box {
    width: fit-content;
    height: fit-content;
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    margin: auto;
    img {
      width: 600px;
      height: auto;
    }
    animation: treasure_chest 2s ease-in-out infinite;
  }
}

@keyframes treasure_chest {
  0% {
    opacity: 1;
    transform: scale(1.1);
  }
  50% {
    opacity: 0.6;
    transform: scale(1);
  }
  100% {
    opacity: 1;
    transform: scale(1.1);
  }
}
</style>
