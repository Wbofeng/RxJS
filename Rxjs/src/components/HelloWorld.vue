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
import Rx from "rxjs/Rx";

export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "Welcome to Your Vue.js App"
    };
  },
  methods: {
    get() {
      // 异步输出
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
        error: err => console.error('something wrong occurred: ' + err),
        complete: () => console.log('done'),
      });
      console.log('just after subscribe'); */
      /* const foo = Rx.Observable.create((observer) => {
        console.log('Hello');
        observer.next(42);
        observer.next(100); // “返回”另外一个值
        observer.next(200); // 还可以再“返回”值
      });

      console.log('before');
      foo.subscribe((x) => {
        console.log(x);
      });
      console.log('after'); */
      // 清除 observable 执行
      /* const observable = Rx.Observable.create((observer) => {
        // 追踪 interval 资源
        const intervalID = setInterval(() => {
          observer.next('hi');
        }, 1000);

        // 提供取消和清理 interval 资源的方法
        return function unsubscribe() {
          clearInterval(intervalID);
        };
      });
      console.log(observable); */
      // 清除 subscription
      /* const observable1 = Rx.Observable.interval(400);
      const observable2 = Rx.Observable.interval(300);

      const subscription = observable1.subscribe(x => console.log('first: ' + x));
      const childSubscription = observable2.subscribe(x => console.log('second: ' + x));

      subscription.add(childSubscription);

      setTimeout(() => {
        // subscription 和 childSubscription 都会取消订阅
        subscription.unsubscribe();
      }, 1000); */
      /* const subject = new Rx.Subject();

      subject.subscribe({
        next: v => console.log('observerA: ' + v), // eslint-disable-line prefer-template
      });
      subject.subscribe({
        next: v => console.log('observerB: ' + v), // eslint-disable-line prefer-template
      });

      const observable = Rx.Observable.from([1, 2, 3, 4]);

      observable.subscribe(subject); */
      // BehaviorSubject
      /* const subject = new Rx.BehaviorSubject(0); // 0是初始值

      subject.subscribe({
        next: v => console.log('observerA: ' + v), // eslint-disable-line prefer-template
      });

      subject.next(1);
      subject.next(2);

      subject.subscribe({
        next: v => console.log('observerB: ' + v), // eslint-disable-line prefer-template
      });

      subject.next(3); */
      // ReplaySubject
      /* const subject = new Rx.ReplaySubject(3); // 为新的订阅者缓冲3个值

      subject.subscribe({
        next: v => console.log('observerA: ' + v), // eslint-disable-line prefer-template
      });

      subject.next(1);
      subject.next(2);
      subject.next(3);
      subject.next(4);

      subject.subscribe({
        next: v => console.log('observerB: ' + v), // eslint-disable-line prefer-template
      });

      subject.next(5); */
      /* const subject = new Rx.ReplaySubject(100, 500);

      subject.subscribe({
        next: v => console.log('observerA: ' + v), // eslint-disable-line prefer-template
      });

      let i = 1;
      setInterval(() => subject.next(i += 1), 200); // eslint-disable-line no-return-assign

      setTimeout(() => {
        subject.subscribe({
          next: v => console.log('observerB: ' + v), // eslint-disable-line prefer-template
        });
      }, 1000); */
      /*  const subject = new Rx.AsyncSubject();

      subject.subscribe({
        next: v => console.log('observerA: ' + v), // eslint-disable-line prefer-template
      });

      subject.next(1);
      subject.next(2);
      subject.next(3);
      subject.next(4);

      subject.subscribe({
        next: v => console.log('observerB: ' + v), // eslint-disable-line prefer-template
      });

      subject.next(5);
      subject.complete(); */
      /* function multiplyByTen(input) {
        const output = Rx.Observable.create(function subscribe(observer) {
          input.subscribe({
            next: v => observer.next(10 * v),
            error: err => observer.error(err),
            complete: () => observer.complete(),
          });
        });
        return output;
      }

      const input = Rx.Observable.from([1, 2, 3, 4]);
      const output = multiplyByTen(input);
      output.subscribe(x => console.log(x)); */
      // 来自一个或多个值
      /*       Rx.Observable.of("foo", "bar");

      // 来自数组
      Rx.Observable.from([1, 2, 3]);

      // 来自事件
      Rx.Observable.fromEvent(document.querySelector("button"), "click");

      // 来自 Promise
      Rx.Observable.fromPromise(fetch("/users"));

      // 来自回调函数(最后一个参数得是回调函数，比如下面的 cb)
      // fs.exists = (path, cb(exists))
      var exists = Rx.Observable.bindCallback(fs.exists);
      exists("file.txt").subscribe(exists =>
        console.log("Does file exist?", exists)
      );

      // 来自回调函数(最后一个参数得是回调函数，比如下面的 cb)
      // fs.rename = (pathA, pathB, cb(err, result))
      var rename = Rx.Observable.bindNodeCallback(fs.rename);
      rename("file.txt", "else.txt").subscribe(() => console.log("Renamed!")); */
    }
  }
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
