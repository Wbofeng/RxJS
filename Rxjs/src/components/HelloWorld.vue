<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2 @click="get">Essential Links</h2>
    <ul>
      <li><a href="https://vuejs.org" target="_blank">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank">Twitter</a></li>
      <br>
      <li><a href="http://vuejs-templates.github.io/webpack/" target="_blank">Docs for This Template</a></li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
      <li><a href="http://router.vuejs.org/" target="_blank">vue-router</a></li>
      <li><a href="http://vuex.vuejs.org/" target="_blank">vuex</a></li>
      <li><a href="http://vue-loader.vuejs.org/" target="_blank">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a></li>
    </ul>
  </div>
</template>

<script>
import Rx from 'rxjs/Rx';

export default {
  name: 'HelloWorld',
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',
    };
  },
  methods: {
    get() {
      /* const observable = Rx.Observable.create((observer) => {
        observer.next(1);
        observer.next(2);
        observer.next(3);
        setTimeout(() => {
          observer.next(4);
          observer.complete();
        }, 1000);
      });

      console.log('just before subscribe');
      observable.subscribe({
        next: x => console.log('got value ' + x), // eslint-disable-line prefer-template
        error: err => console.error('something wrong occurred: ' + err), // eslint-disable-line prefer-template
        complete: () => console.log('done'),
      });
      console.log('just after subscribe'); */

      const foo = Rx.Observable.create((observer) => {
        console.log('Hello');
        observer.next(42);
        observer.next(100); // “返回”另外一个值
        observer.next(200); // 还可以再“返回”值
      });

      console.log('before');
      foo.subscribe((x) => {
        console.log(x);
      });
      console.log('after');
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
