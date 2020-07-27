<template>
  <div class="calc">
    <div class="display">{{number || "0"}}</div>
    <div @click="clear" class="btn special delete">C</div>
    <div @click="remove" class="btn special delete">DEL</div>
    <div class="btn special">+/-</div>
    <div class="btn special">%</div>
    <div @click="append('7')" class="btn">7</div>
    <div @click="append('8')" class="btn">8</div>
    <div @click="append('9')" class="btn">9</div>
    <div @click="multiplication" class="btn special">*</div>
    <div @click="append('4')" class="btn">4</div>
    <div @click="append('5')" class="btn">5</div>
    <div @click="append('6')" class="btn">6</div>
    <div @click="substraction" class="btn special">-</div>
    <div @click="append('1')" class="btn">1</div>
    <div @click="append('2')" class="btn">2</div>
    <div @click="append('3')" class="btn">3</div>
    <div @click="addition" class="btn special">+</div>
    <div @click="append('0')" class="btn zero">0</div>
    <div @click="dot" class="btn">.</div>
    <div @click="division" class="btn special">/</div>
    <div @click="pi" class="btn special pi">PI</div>
    <div @click="sqrt" class="btn special radical">
      <span>
        √
        <span style="border-top:2px solid; position: relative; top: 3px; right: 10px">x</span>
      </span>
    </div>
    <div @click="equal" class="btn special equal">=</div>
  </div>
</template>

<script>
export default {
  name: "Calculator",

  data() {
    return {
      prevNum: null,
      number: "",
      operator: null,
      operatorClicked: false,
    };
  },

  methods: {
    clear() {
      this.number = "";
    },

    append(num) {
      if (this.operatorClicked) {
        (this.number = ""), (this.operatorClicked = false);
      }
      // this.number = `${this.number}${num}`;
      if (this.number.length > 8) {
        let result = `${this.number}${num}`;
        this.number = result.slice(0, -1);
      } else if (this.number.length <= 9) {
        this.number = `${this.number}${num}`;
      }
      // if (this.number.indexOf(".") === -1) {
      //   this.number = `${this.number}${num}`;
      // } else {
      //   return this.number.toFixed(2);
      // }
    },

    dot() {
      if (this.number.indexOf(".") === -1) {
        this.append(".");
      }
    },

    remove() {
      this.number = this.number.slice(0, -1);
    },

    setPrevNum() {
      this.prevNum = this.number;
      this.operatorClicked = true;
    },

    addition() {
      this.operator = (a, b) => a + b;
      this.setPrevNum();
    },

    substraction() {
      this.operator = (a, b) => a - b;
      this.setPrevNum();
    },

    multiplication() {
      this.operator = (a, b) => a * b;
      this.setPrevNum();
    },

    division() {
      this.operator = (a, b) => a / b;
      this.setPrevNum();
    },

    pi() {
      const pi = Math.PI;
      this.number = pi.toFixed(4);
    },

    sqrt() {
      this.number = Math.sqrt(this.number);
    },

    equal() {
      if (this.operator === null) {
        return this.number;
      }
      let result = `${this.operator(
        parseFloat(this.prevNum),
        parseFloat(this.number)
      )}`;
      this.number = parseFloat(result).toFixed(2);

      if (this.number.length > 9) {
        this.number = "E";
      }

      this.prevNum = "";
    },
  },
};
</script>

<style scoped>
.calc {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  margin: 0 auto 100px auto;
  padding: 10px;
  width: 400px;
  /* height: 550px; */
  font-size: 40px;
  border: 2px solid grey;
  border-radius: 8px;
  box-shadow: 10px 10px 10px 10px #2c3e50;
  background-color: honeydew;
}

.display {
  grid-column: 1/5;
  background-color: #333;
  color: #fff;
  padding: 20px;
  border-radius: 5px;
}

.btn {
  background-color: #f2f2f2;
  border: 1px solid #999;
  cursor: pointer;
  border-radius: 5px;
  padding: 20px;
}

.btn:hover {
  background-color: #2c3e50;
  color: #f2f2f2;
  cursor: pointer;
}

.special {
  background-color: #35495e;
  color: #43b883;
}

.special:hover {
  background-color: #43b883;
  color: #35495e;
}

.delete {
  background-color: tomato;
  color: white;
}

.delete:hover {
  background-color: red;
  color: yellow;
}

.equal {
  grid-column: 3/5;
  background-color: #ebd515;
  color: #35495e;
}

.pi {
  background-color: #43b883;
  color: #35495e;
}

.pi:hover {
  background-color: #35495e;
  color: #43b883;
}

.radical {
  background-color: #43b883;
  color: #35495e;
}

.radical:hover {
  background-color: #35495e;
  color: #43b883;
}

.zero {
  grid-column: 1/3;
}
</style>
