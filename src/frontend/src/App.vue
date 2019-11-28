<template>
  <div>
    {{ message }}
    <br/>
    <span :title="message">
      내 위에 잠시 마우스를 올리면 동적으로 바인딩 된 title을 볼 수 있습니다!
    </span>
    <p v-if="seen">이제 나를 볼 수 있어요</p>
    <ol>
      <li
          v-for="todo in todos"
          :key="todo.id"
      >
        {{ todo.text }}
      </li>
    </ol>
    <div>
      <button @click="reverseMessage">메시지 뒤집기</button>
    </div>
    <div>
      <input v-model="message">
    </div>
    <HelloWorld></HelloWorld>
  </div>
</template>

<script>
  import HelloWorld from './components/HelloWorld'

  export default {
    name: 'App',
    comments: {
      HelloWorld,
    },
    data() {
      return {
        message: 'hi',
        seen: true,
        todos: [
          {
            id: 1,
            text: 'JavaScript 배우기',
          },
          {
            id: 2,
            text: 'Vue 배우기',
          },
          {
            id: 3,
            text: '무언가 멋진 것을 만들기',
          },
        ],
      }
    },
    methods: {
      reverseMessage: function () {
        this.message = this.message.split('').reverse().join('');
      }
    },
    created() {
      window.console.log('create');
    },
    mounted() {
      window.console.log('add dom');
    }
  };
</script>
