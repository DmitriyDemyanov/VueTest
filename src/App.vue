<template>
  <div id="app" class="my-class">
    <h1 class="title"
    :class="[classObj,activeClass]"
    :style="{'font-size': fontSize + 'px'}">{{firstName}}</h1>
    <h2>{{num +2}}</h2>
    <h3>{{obj.age}}</h3>
    <a :href="linkUrl">Google</a>
    <p> <br> </p>
    <a :[attrKey]="linkUrl">Google</a>

    <template v-if="msgIsVisible === 1">
      <div class="message" >Some message!</div>
    </template>

    <template v-else-if= "msgIsVisible === 2">
      <div class="message">Else message</div>
    </template>
    <template v-else>
      <div class="message" >Another message!</div>
    </template>
    <div v-show="isVisiibleBlock"> V show message</div>

    <!-- <div class="name-input" v-if="inputNameVisible">
      <label>Name</label>
      <input type="text" placeholder="input name" key="input-name">
    </div>

    <div class="nickname-input" v-else>
      <label>Nickname</label>
      <input type="text" placeholder="input nickname" key="input-nickname">
    </div> -->

    <!-- <button @click="inputNameVisible = !inputNameVisible"></button> -->

    <!-- <button @click.right="onClick('some value', $event)">Click event</button>
    <a href="#" @click.prevent="onLinkClick">Link</a> -->

    <label for="my-input">
      Nickname
      <input id="my-input" type="text" @keyup.enter="onKeyUp">
    </label>
    <h1>{{text}}</h1>

    <ul>
      <!-- <li v-for="(color, index) in colors" :key="index"> {{index + 1 }} {{ color }} </li> -->

    <!-- <li v-for="user in users" :key="user.id">
      {{user.id}}{{ user.name }}{{ user.age }}</li> -->

    <li v-for="(value, name, index) in product" :key="value">
       {{index + 1}}- {{ name }} --- {{ value }} </li>

      <div> -->
        <input  type="text" @keyup.enter="deleteProp">
        <!-- <input type="text" @keyup.enter="addNewColor"> -->
      </div>

      </ul>

      <HelloWorld :user-object="obj" :title="title" @onChangeCounter="onChangeCounterIsComponent" />

      <input type="text" v-model="textComputed">
      <h3>
        Input text value:
        <i>{{  text }}</i>
      </h3>
      <div class="checkboxes">
        <input type="checkbox" v-model="checkbox">
        <h3>
          checkbox value:
        <i>{{  checkbox }}</i>
      </h3>

      <input type="checkbox" v-model="checkboxArray" value="one">
      <input type="checkbox" v-model="checkboxArray" value="two">
      <input type="checkbox" v-model="checkboxArray" value="three">
      <h3>
          checkbox value:
        <i>{{  checkboxArray }}</i>
      </h3>
      </div>
      <select v-model="select">
        <option value="bmw">BMW</option>
        <option value="audi">AUDI</option>
        <option value="porshe">PORSHE</option>
      </select>
      <h3>
          select value:
        <i>{{  select }}</i>
      </h3>
  </div>
</template>

<script>

import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
  },

  data: () => ({
    colors: ['orange', 'black', 'yellow'],
    users: [{ name: 'Dima', age: 25, id: '1' }, { name: 'Ivan', age: 30, id: '2' }],
    text: '',
    checkbox: false,
    checkboxArray: [],
    select: '',
    title: 'Some text',
    num: 2,
    obj: {
      name: 'Dima',
      age: 30,
    },
    linkUrl: 'https://google.com',
    attrKey: 'href',
    msgIsVisible: 2,
    isVisiibleBlock: false,
    inputNameVisible: false,
    product: {
      brand: 'apple',
      model: 'iphone 11',
      price: '$1000',
    },
    firstName: 'Dima',
    lastName: 'Demyanov',
    activeClass: 'my-active-class',
    isActive: false,
    fontSize: 30,
  }),
  computed: {
    classObj() {
      return {
        'active-class': this.isActive,
        error: !this.isActive,

      };
    },
    textComputed: {
      get() {
        return this.text;
      },
      set(value) {
        console.log(value);
        this.text = value;
      },
    },
  },

  methods: {
    onChangeCounterIsComponent(value) {
      console.log('In Appvue, counter:', value);
      this.isActive = value % 2 !== 0;
    },
    addNewColor(e) {
      // this.colors.push(e.target.value);
      // this.colors[this.colors.length] = e.target.value;
      this.$set(this.colors, this.colors.length, e.target.value);
    },
    onClick(value, e) {
      console.log(value, e);
    },
    onLinkClick() {
      console.log('link click');
    },
    onKeyUp(e) {
      this.text = e.target.value;
    },
    deleteProp(e) {
      // delete this.product[e.target.value];
      this.$delete(this.product, e.target.value);
    },

  },

};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.error {
  color: red;
}
</style>
