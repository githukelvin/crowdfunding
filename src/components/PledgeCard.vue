<script>
export default {
  data() {
    return {
      price1: 25,
      price2: 75,
      price3: 200,
      p1: "",
      p2: "",
      p3: "",
      mod: "",
      modt: "",
      left: [101, 64],
      divs: [],
    };
  },
  methods: {
    update() {
      this.price1 = this.p1;
      this.price2 = this.p2;
      this.price3 = this.p3;
      if (this.price1 <= 25) {
        this.price1 = 25;
      }
      if (this.price2 <= 75) {
        this.price2 = 75;
      }
      if (this.price3 <= 200) {
        this.price3 = 200;
      }
    },

    selected() {
      let pre = document.querySelector(".active");
      // console.log(this.divs)
      if (pre == null) {
        this.divs.forEach((div) => {
          div.addEventListener("click", () => {
            div.classList.add("active");
          });
        });
      } else {
        pre.classList.remove("active");
        this.divs.forEach((div) => {
          div.addEventListener("click", () => {
            div.classList.add("active");
          });
        });
      }
    },
    close() {
      this.mod.style.display = "none";
      this.modt.style.display = "flex";
    },
  },
  mounted() {
    let modal = document.querySelector(".modal");
    let modalt = document.querySelector(".modalt");
    this.mod = modal;
    this.modt = modalt;
    let top = document.querySelectorAll(".top");
    this.divs = [...top];
  },
};
</script>

<template>
  <div class="list">
    <div class="top" @click="selected(event)">
      <div class="com">
        <div class="upper">
          <div class="radio">
            <div class="circle">
              <div class="dot"></div>
            </div>
          </div>
          <div class="right">
            <div class="up">
              <div class="info">
                <div class="pledge">
                  <div class="more">
                    <h2>Pledge with no reward</h2>
                  </div>
                </div>
                <p class="para">
                  Choose to support us without a reward if you simply believe in
                  our project. As a backer, you will be signed up to receive
                  product updates via email.
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="top" @click="selected(event)">
      <div class="com">
        <div class="upper">
          <div class="radio">
            <div class="circle">
              <div class="dot"></div>
            </div>
          </div>
          <div class="right">
            <div class="up">
              <div class="info">
                <div class="pledge">
                  <div class="more">
                    <h2>Bamboo Stand</h2>
                    <p>Pledge $25 or more</p>
                  </div>
                  <h1>
                    {{ left[0] }}
                    <span>left</span>
                  </h1>
                </div>
                <p class="para">
                  You get an ergonomic stand made of natural bamboo. You've
                  helped us launch our promotional campaign, and you’ll be added
                  to a special Backer member list.
                </p>
              </div>
            </div>
          </div>
        </div>
        <hr />
        <div class="low">
          <input
            type="text"
            @input="update"
            v-model.number="p1"
            name="text"
            id="text"
            placeholder="Enter your pledge"
          />
          <div class="controls">
            <div class="amount">
              <p>$</p>
              <h2>{{ price1 }}</h2>
            </div>
            <button class="" @click="close" id="con">Continue</button>
          </div>
        </div>
      </div>
    </div>
    <div class="top" @click="selected(event)">
      <div class="com">
        <div class="upper">
          <div class="radio">
            <div class="circle">
              <div class="dot"></div>
            </div>
          </div>
          <div class="right">
            <div class="up">
              <div class="info">
                <div class="pledge">
                  <div class="more">
                    <h2>Black Edition Stand</h2>
                    <p>Pledge $75 or more</p>
                  </div>
                  <h1>
                    {{ left[1] }}
                    <span>left</span>
                  </h1>
                </div>
                <p class="para">
                  You get a Black Special Edition computer stand and a personal
                  thank you. You’ll be added to our Backer member list. Shipping
                  is included.
                </p>
              </div>
            </div>
          </div>
        </div>
        <hr />
        <div class="low">
          <input
            type="text"
            @input="update"
            v-model.number="p2"
            name="text"
            id="text"
            placeholder="Enter your pledge"
          />
          <div class="controls">
            <div class="amount">
              <p>$</p>
              <h2>{{ price2 }}</h2>
            </div>
            <button class="" @click="close" id="con">Continue</button>
          </div>
        </div>
      </div>
    </div>
    <div class="top" @click="selected(event)" id="buz">
      <div class="com">
        <div class="upper">
          <div class="radio">
            <div class="circle">
              <div class="dot"></div>
            </div>
          </div>
          <div class="right">
            <div class="up">
              <div class="info">
                <div class="pledge">
                  <div class="more">
                    <h2>Mahogany Special Edition</h2>
                    <p>Pledge $200 or more</p>
                  </div>
                  <h1>
                    0
                    <span>left</span>
                  </h1>
                </div>
                <p class="para">
                  You get two Special Edition Mahogany stands, a Backer T-Shirt,
                  and a personal thank you. You’ll be added to our Backer member
                  list. Shipping is included.
                </p>
              </div>
            </div>
          </div>
        </div>
        <hr />
        <div class="low">
          <input
            type="text"
            @input="update"
            v-model.number="p3"
            name="text"
            id="text"
            placeholder="Enter your pledge"
          />
          <div class="controls">
            <div class="amount">
              <p>$</p>
              <h2>{{ price3 }}</h2>
            </div>
            <button class="" @click="close" id="con">Continue</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.list {
  display: flex;
  flex-direction: column;
  gap: 1.33em;
}
.active {
  border: 1px solid hsl(176, 50%, 47%);

  hr {
    display: block;
  }
  .low {
    display: flex;
  }
  .com .upper .radio .circle .dot {
    display: block;
  }
}
.top:hover {
  border: 1px solid hsl(176, 50%, 47%);
}
hr {
  height: 2px;
  width: 130%;
  margin-left: -3em;
  display: none;
  background: rgba(151, 145, 145, 0.336);
}
.com {
  cursor: pointer;
  display: flex;
  flex-direction: column;
  padding: 2em 0.5em 2em 1.85em;
  overflow: hidden;

  .upper {
    display: flex;
    flex-direction: row;
    gap: 1.3em;
    align-items: flex-start;
    padding-right: 0.3em;
    margin-top: -0.1em;
    .radio {
      .circle {
        width: 25px;
        height: 25px;
        border-radius: 50%;
        background: #fff;
        display: grid;
        place-items: center;
        border: 1px solid hsl(0, 0%, 48%);
        &:hover {
          border: 1px solid hsl(176, 50%, 47%);
        }
        .dot {
          width: 13px;
          height: 13px;
          border-radius: 50%;
          background: hsl(176, 50%, 47%);
          display: none;
        }
      }
    }
  }
}
.upper .right {
  .up {
    display: flex;
    flex-direction: row;
    .info {
      display: flex;
      flex-direction: column;
      .pledge {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        .more {
          display: flex;
          flex-direction: row;
          gap: 1em;
          align-items: center;
          h2 {
            font-family: "bold";
            color: #000;
            &:hover {
              color: hsl(176, 50%, 47%);
            }
          }
          p {
            font-family: "bold";
            color: hsl(176, 50%, 47%);
          }
        }
        h1 {
          display: flex;
          align-items: center;
          font-family: "bold";
          font-size: 1.1em;
          gap: 0.5em;
          span {
            font-family: "regular";
            color: hsl(0, 0%, 48%);
            font-size: 0.8em;
          }
        }
      }
      .para {
        margin-top: 1.05em;
        font-family: "regular";
        color: hsl(0, 0%, 48%);
        line-height: 1.9;
        font-size: 0.95em;
      }
    }
  }
}
.low {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  margin-top: 1.5em;
  align-items: center;
  gap: 1.9em;
  display: none;

  input {
    width: 100%;
    height: 100%;
  }
  .controls {
    display: flex;
    align-items: center;
    gap: 0.5em;
    .amount {
      display: flex;
      align-items: center;
      border: 1px solid hsl(0, 0%, 48%);
      padding: 0.8em 3em 0.8em 1em;
      gap: 0.4em;
      border-radius: 30px;
      &:hover {
        border: 1px solid hsl(176, 50%, 47%);
      }

      p {
        color: hsl(0, 0%, 48%);
        font-family: "medium";
        font-size: 0.9em;
      }
      h2 {
        font-size: 0.9em;
        color: #000;
        font-family: "bold";
      }
    }
  }
  button {
    background: hsl(176, 50%, 47%);
    border-radius: 30px;
    padding: 1em 1.75em;
    color: white;
    font-family: "bold";
    font-size: 0.9em;
    cursor: pointer;
    &:hover {
      background: hsl(176, 72%, 28%);
    }
  }
}
@media screen and (max-width: 480px) {
  .com{
    padding-bottom:3.5em;
  }
  .upper .right .up .info {.pledge {
    position:relative;
    .more {
      flex-direction: column;
    }
  }
  .para{
    margin-left:-3em;
  }
}
  h1 {
    position:absolute;
    left:-3em;
    bottom:-200px;
  }
}
@media screen and (max-width:480px){
  .low{
    flex-direction:column;
    gap:1em;
    // margin-top: 3em;
    .controls{
      flex-direction:row;
      gap:1em;
      
    }
  }
  hr{
    margin-top:4em;
  }
    h1 {
    position:absolute;
    left:-3em;
    bottom:-180px;
  }
  
}
</style>
