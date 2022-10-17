<template>
  <div id="app" class="my-class">
    <h1>{{firstName}}</h1>
    <h2>{{num +2}}</h2>
    <h3>{{num > 1 ? 'number: > 1' : 'number < 1'}}</h3>
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

    <button @click.right="onClick('some value', $event)">Click event</button>
    <a href="#" @click.prevent="onLinkClick">Link</a>

    <label for="my-input">
      Nickname
      <input id="my-input" type="text" @keyup.enter="onKeyUp">
    </label>
    <h1>{{text}}</h1>

  </div>
</template>

<script>
import UserName from './components/UserName.vue';
import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
    UserName,
  },

  data: () => ({
    text: '',
    firstName: 'Dima',
    num: 2,
    obj: {
      age: 30,
    },
    linkUrl: 'https://google.com',
    attrKey: 'href',
    msgIsVisible: 2,
    isVisiibleBlock: false,
    inputNameVisible: false,
  }),

  methods: {
    onClick(value, e) {
      console.log(value, e);
    },
    onLinkClick() {
      console.log('link click');
    },
    onKeyUp(e) {
      console.log(e);
      this.text = e.target.value;
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
</style>
