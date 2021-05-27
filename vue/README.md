# Attribute
## data
Function trả về variable của component


Methods có thể dùng variable bằng cách thông qua this
```... this.tên_variable ...```

## methods
Object chứa các methods của component
- Method có thể call ở bất kì function nào trong component
- Method để xử lý event

## computed
Method return value dùng để thay thế data
- Dành cho những biến hay thay đổi trong component
```

computed: {
  show: { //tên object
    get() { //khi 1 thằng nào đó lấy value của show, nó sẽ lấy returned value từ get()
      //process
      return value
    }
    set(newValue) {//khi 1 thằng gán value cho show : show = newValue, newValue sẽ truyền vào set
      //process
    }
  }
}
```

## watched
Quan sát sự thay đổi của 1 data

## mixin
Ghép các tính chất của 1 component vào component khác
```

import mixin1 from ...
import mixin2 from ...

export default {
  mixins: [
    mixin1,
    mixin2
  ]
}
//component có thể dùng mọi thứ trong mixin như là của riêng component
```

## props
Data nhận từ parent component.

không được gán giá trị vào `props`

Khai báo không quan tâm data type
```
props: ['data1', 'data2',...]
```

Khai báo quan tâm data type
```
props: {
  prop_name: prop_type,
  title: String,
  likes: Number,
  isPublished: Boolean,
  commentIds: Array,
  author: Object
}
```

Khai báo có default value
```
props: {
  props_name: {
    type: data_type,
    default: default_value
  }
}
```

Khai báo prop như 1 attribute của component
```
//trong child component
props: {
  open: {
    type: Boolean, //Boolean dùng tốt nhất
    default: false, //để false để tắt khi không khai báo
    required: true // để true để thay đổi value = default:false sang true
  }
}

//trong parent component
<child-component open></child-component> //chỉ cầng gọi lên thì open == true
```

# Lifecycle
![lifecycle](lifecycle.png)


1. beforeCreate : trước khi load data và init events của Vue.

1. created : sau khi khởi tạo Vue xong, trước khi compile template.

1. beforeMount : trước khi dịch từ template của Vue sang code HTML, CSS, JS

1. mounted : sau khi dịch template của Vue, sau khi quét thay đổi của data.

1. beforeUpdate : trước khi thay đổi template.

1. updated : ngay sau khi thay đổi template.

1. beforeDestroy : trước khi tắt toàn bộ các thành phần của Vue.

1. destroyed : sau khi đã tắt hết thành phần, chuẩn bị thoát.

# Event
Truyền data từ child component to parent component thì sử dụng hàm $emit
- Tạo event để truyền data từ child component ra ngoài
```
# Child component
export default : {
  methods: {
    tên_method (paramester) {
      ...
      this.$emit('tên_event', value_output)
      ...
    }
  }
  ...
}

# Parent component
<template> 
  <child-component @tên_event="tên_var = $event"> </child-component>
  ...
</template>
```

Tạo v-model
```
# Child
export default : {
    props: {
        value: Datatype //bắt buộc phải có props 'value'
    },
    methods: {
        methodA() {
            this.$emit('input', value) //bắt buộc phải có event 'input'
        }
    }
}

# Parent 
<template> 
  <child-component @v-model="data"> </child-component>
  ...
</template>
```

# Router
Định tuyến cho component trong App.vue.

The default mode for vue-router is hash mode 
- it uses the URL hash to simulate a full URL so that the page won't be reloaded when the URL changes.
- Khi thay đổi URL => chỉ thay đổi component với `<router-view/>` => không reload trang

1. Tạo routes.js chứa định tuyến
```
// Define routes to component
import Home from './components/Home.vue'
import User from './components/user/User.vue'
export const routes = [
    { path: '/', name: 'homepage', component: Home },
    { path: '/user', name: 'user', component: User }
]
```

1. Import vue-router trong main.js :
```

import VueRouter from 'vue-router'
import { routes } from './routes'

Vue.use(VueRouter)
const router = new VueRouter({
  routes //truyền routes đã tạo VueRouter
})

new Vue({
  el: '#app',
  router, //sử dụng router trong Vue
  render: h => h(App)
})
```

1. Gọi `<router-view/>` trong App.vue
```
<template>
  <div id="app">
    <div class="col-xs-12 col-sm-8 offset-sm-2 col-md-6 offset-md-3 text-left">
      <h1>Vue Router</h1>
      <hr>
      <router-view/>
    </div>
  </div>
</template>
```

## `<router-link>`
thay thế cho tag để điều hướng Router.
```
<a href="..." class="class"> Content </a>
//Thay thế bằng
<router-link tag="a" class="class" to="path_đã_tạo"> Component </router-link>
```
- Thêm active-class cho `<router-link>`
```
<router-link
    class="nav-item"
    tag="li"
    to="/user"
    active-class="active"
>
    <a class="nav-link"> User </a>
</router-link>
```
- Tạo một method thay thế `<router-link>`
```

<template>
    <div>
        <h1>User</h1>
        <button class="btn btn-danger" @click="backHome"> Back to Home</button>
    </div>
</template>
<script>
export default {
    methods: {
        backHome() {
            this.$router.push('/')// = <router-link to="/">, gọi bằng path
            this.$router.push({ name: 'homepage' }) //Gọi = tên
        }
    }
}
</script>
```

## Truyền argument vào `path`
```

// routes.js
export const routes = [
   ...
    { path: '/user/:id', name: 'admin', component: UserDetail }, //truyền id vào
    { path: ':id/edit', name: 'useredits', component: UserEdit }
]

//trong component UserDetail và cả UserEdit (chỉ cần trong link có truyền vào id thì thằng nào cũng lấy được.
export default {
    methods: {
        ...
        goDetails() {
            this.$router.push('/user/abc')//gọi kèm theo argument
            this.$router.push({ name: 'userdetails', params: {id: 'abc'} })//gọi kèm theo argument
        }
    }
}
```

Lấy parameters từ route
```
data () {
    return {
        id : this.$route.params.id //lấy parameters của $route
    }
},
```

## Child Router
Tạo child path trong routes.js
```
export const routes = [
    { path: '/', name: 'homepage', component: Home },
    { path: '/user', name: 'user', component: User, children: [
        { path: '', name: 'index', component: UserStart },
        { path: ':id', name: 'userdetails', component: UserDetail },
        { path: ':id/edit', name: 'userdetails', component: UserEdit },
    ]},
]
```

Gọi child component với `<route-view>`
```
//parent component
<template>
    <div class="mt-3">
        <h1 class="text-center">User</h1>
        <button class="btn btn-success text-center btn-block" @click="backHome"> Back to Home </button>
        <router-view/>
    </div>
</template>

//trong component UserStart ở example trên 
<ul class="list-group">
    <router-link
        tag="li"
        v-for="user in users"
        :key="user.id"
        :to="'/user/' + user.id"
        class="list-group-item"
        style="cursor: pointer"
    >User id : {{ user.id }}</router-link>
</ul>
//=> khi click vào bất kì route-link nào thì child component sẽ thay thế route-view trong parent component
```

## Redirect
```
{ path: '/auth-redirect', redirect: { name: 'homepage' } }
```

Khi nhập sai link sẽ chuyển qua error component
```
{ path: '*', redirect: { name: 'errorage' } } // * đại diện cho tất cả các path chưa được khai báo
```

# Vuex
Vuex = state management pattern + library
- Lưu trữ variables chung cho cả project => tất cả các components đều có thể dùng variables đó.

## State
```
//Cấu trúc của 1 Vue
new Vue({
  // view
  template: `
    <div>{{ count }}</div>
  `,
  // state
  data () {
    return {
      count: 0
    }
  },
  // actions
  methods: {
    increment () {
      this.count++
    }
  }
})
```

The state
- The source of truth that drives our app.
- Đó là biến thực sự của app

The view
- Which is just a declarative mapping of the state.
- Result của state.get()

The actions
- The possible ways the state could change in reaction to user inputs from the view.
- Các function → state.set()

![Vuex](Vuex.png)

Vuex là quản lý những state dùng chung.
- Tạo 1 state
```
//trong store.ts
export default new Vuex.Store({
  state: {
    result: 0 //tạo 1 status chung cho toàn project với default value
  }
})

//có thể get/set trực tiếp state ở bất kì component nào
<script>
export default {
  methods: {
    increament () {
      this.$store.state.result++
    },
    decreament () {
      this.$store.state.result--
    }
  }
}
</script>
``` 
- Khi một component thay đổi 1 state thì các components khác dùng state đó cũng thay đổi.

## Getters
Là những function chuyên để return value từ `vuex` sau khi process.
- Paramester thường là `state` để sử lý data chung của project.
```
//trong store.ts
export default new Vuex.Store({
  state: {
    result: 0
  },
  getters: {
    tenResult: state => {
      return state.result * 10
    }
  }
})

//trong component
tenResult () {
  return this.$store.getters.tenResult
}
```

mapGetters
- Để giảm thiểu code và component dùng trực tiếp các getters thì dùng qua `mapGetters`
- `mapGetters` là một hàm của `Vuex` → lấy các getter của `store.js`
```
//trong component
<template>
    <div>
      <!-- <p>This is the results : {{ result }}</p> -->
      <p>This is the results : {{ getResult }}</p>
      <br>
      <p>There is ten times of results : {{ tenResult }}</p>
    </div>
</template>

//case 1
<script>
import { mapGetters } from 'vuex'
export default {
  computed: {
    ...mapGetters([ //lấy toàn bộ thuộc tính của getters
      'getResult', //các getter sẽ được lấy
      'tenResult'
    ])
  }
  
}
</script>
```

## Mutation
Là những functions sử lý thay đổi state
```
mutations: {
  name_func(
    state, //luôn bắt đầu 1 mutation = state
    payload) 
  {
    ...sửa lý thay đổi các biến trong state dựa theo payload
  }
}
```

Commit
- Là function để component gọi 1 mutation
```

//trong store.ts
export default new Vuex.Store({
  mutations: {
    increamentOp (state, n) { //tăng theo một số n nào đó
      state.result += n
    }
  },
})

//trong component
<script>
export default {
  methods: {
    increament () {
      //gọi mutation thông qua commit, truyền giá trị của n vào.
      this.$store.commit(
        'increamentOp', //tên của mutation 
        30              //payload
      ) 
    }
  }
}
</script>
```
- Dùng trực tiếp mutations qua mapMutations

## Acitions
Giống mutation nhưng có thể chạy acsynchronous

# Question
## Các tính năng chính của VueJS là gì?
1. Virtual DOM: Nó sử dụng DOM ảo tương tự như các framework hiện có khác như ReactJS, Ember, v.v. Virtual DOM là một đại diện cây trong bộ nhớ có dung lượng nhẹ của DOM HTML gốc và được cập nhật mà không ảnh hưởng đến DOM gốc.
1. Component: Được sử dụng để tạo các phần tử tùy chỉnh có thể tái sử dụng trong các ứng dụng VueJS.
1. Template: VueJS cung cấp các template dựa trên HTML liên kết DOM với dữ liệu.
1. Định tuyến (routing): Điều hướng giữa các trang được thực hiện thông qua vue-router.
1. Nhẹ (light-weight): VueJS là thư viện có trọng lượng nhẹ so với các framework khác.

## Vue instance là gì?
Cá thể Vue, thường được gọi là vm trong ứng dụng Vue là ViewModel của mẫu MVVM mà Vue tuân theo. 

## Lifecycle methods || Lifecycle hooks của vue là gì
Lifecycle hooks là những callback được gọi từng giai đoạn của runtime của vue
## 1. Creation (Initialization)
Init vue instance.
- Creation hooks thực hiện action trước khi components gán vào DOM.
- Chỉ mỗi creation hooks có thể chạy ở server side
1. `beforeCreate`
Chạy trước khi init component
- Setup observer cho data
  - Mới là observer chưa có default value
- Init events trong component
```javascript
  new Vue({
    data: {
      count: 10
    },
    beforeCreate: function () {
      console.log('Nothing gets called at this moment')
      // `this` points to the view model instance
      console.log('count is ' + this.count);
    }
  })
      // count is undefined
```
2. `created`
Gọi sau khi setup xong events + data observation
- Có thể active event
- Có thể gán giá trị cho data
```javascript
  new Vue({
    data: {
      count: 10
    },
    created: function () {
      // `this` points to the view model instance
      console.log('count is: ' + this.count)
    }
  })
  // count is: 10
```
Nhưng component vẫn chưa được mount nên không thể access vào template được

*Note:* Sẽ không thể access vào DOM hoặc target mounting element (this.$el) vì chưa gán component với DOM
## 2. Mounting (DOM Insertion)
Lần render đầu tiên
- Gán component vào DOM
1. `beforeMount`
Trước khi first render
```javascript
  new Vue({
    beforeMount: function () {
      // `this` points to the view model instance
      console.log(`this.$el is yet to be created`);
    }
  })
```
2. `mounted`
Sau khi first render
-  full access to the reactive component, templates, and rendered DOM (via. this.$el)
```javascript
  <div id="app">
      <p>I’m text inside the component.</p>
  </div>
  new Vue({
    el: ‘#app’,
    mounted: function() {
      console.log(this.$el.textContent); // I'm text inside the component.
    }
  })
```
## 3. Updating (Diff & Re-render)
Data changes dẫn đến update component => re-render
1. `beforeUpdate`
- runs after data changes on your component, 
- right before the DOM is patched and re-rendered
```javascript
  <div id="app">
    <p>{{counter}}</p>
  </div>
  ...// rest of the code
  new Vue({
    el: '#app',
    data() {
      return {
        counter: 0
      }
    },
      created: function() {
      setInterval(() => {
        this.counter++
      }, 1000)
    },

    beforeUpdate: function() {
      console.log(this.counter) // Logs the counter value every second, before the DOM updates.
    }
  })
```
2. `updated`
- after data changes on your component and the DOM re-renders.
```javascript
  <div id="app">
    <p ref="dom">{{counter}}</p>
  </div>
  ...//
  new Vue({
    el: '#app',
    data() {
      return {
        counter: 0
      }
    },
      created: function() {
      setInterval(() => {
        this.counter++
      }, 1000)
    },
    updated: function() {
      console.log(+this.$refs['dom'].textContent === this.counter) // Logs true every second
    }
  })
```

## 4. Destruction (Teardown)
Perform actions when your component is destroyed
- Cleanup
- Analytics sending
1. `beforeDestroy`
- fired right before teardown
- cleanup events or reactive subscriptions
```javascript
  new Vue ({
    data() {
      return {
        message: 'Welcome VueJS developers'
      }
    },

    beforeDestroy: function() {
      this.message = null
      delete this.message
    }
  })
```

2. `destroyed`
after your component has been destroyed
- its directives have been unbound
- its event listeners have been removed
```javascript
  new Vue ({
    destroyed: function() {
      console.log(this) // Nothing to show here
    }
  })
```

## Khác biệt giữa v-if và v-show
1. Render
- v-if chỉ render element khi thỏa mãn condition
  - Xóa element khỏi DOM khi không thỏa mãn
  - Component created khi `v-if = true`
  - Component destroyed khi khi `v-if = false`
- v-show chỉ dùng CSS để ẩn element
  - Element vẫn tồn tại trong DOM
1. v-else chỉ dùng cho v-if
  - else-if cũng chỉ cho v-if
1. 
1. v-if supports <template> tab but v-show doesn't support.

## Tại sao khi bind v-for thường phải mapping key
- Để khi 1 item trong array update thì sẽ tìm và update view tương ứng mà không phải update cả array

## What is the purpose of v-for directive
loop through items in an array or object

1. **Array usage:**
```javascript
<ul id="list">
  <li v-for="(item, index) in items">
    {{ index }} - {{ item.message }}
  </li>
</ul>

var vm = new Vue({
  el: '#list',
  data: {
    items: [
      { message: 'John' },
      { message: 'Locke' }
    ]
  }
})
```
You can also use `of` as the delimiter instead of `in`, similar to javascript iterators.

2. **Object usage:**
```javascript
<div id="object">
  <div v-for="(value, key, index) of user">
    {{ index }}. {{ key }}: {{ value }}
  </div>
</div>

var vm = new Vue({
  el: '#object',
  data: {
    user: {
      firstName: 'John',
      lastName: 'Locke',
      age: 30
    }
  }
})
```

## Why should not use if and for directives together on the same element?
It is recommended not to use v-if on the same element as v-for. 
- Because v-for directive has a higher priority than v-if.
```javascript
  <ul>
    <li
      v-for="user in users"
      v-if="user.isActive"
      :key="user.id"
    >
      {{ user.name }}
    <li>
  </ul>
```

```javascript
  <ul v-if="shouldShowUsers">
    <li
      v-for="user in users"
      :key="user.id"
    >
      {{ user.name }}
    <li>
  </ul>
```

## When component needs a single root element?
In VueJS 2.x, every component must have a single root element **when template has more than one element**. In this case, you need to wrap the elements with a parent element.
```vue
<template>
  <div class="todo-item">
      <h2>{{ title }}</h2>
      <div v-html="content"></div>
  </div>
</template>
```
Otherwise there will an error throwing, saying that "Component template should contain exactly one root element...".

Whereas in 3.x, components now can have multiple root nodes. This way of adding multiple root nodes is called as fragments.
```vue
<template>
    <h2>{{ title }}</h2>
    <div v-html="content"></div>
</template>
```

## What is the data flow followed by props?
`props` là 1 way down
- Không thể gán giá trị cho props

## What is vue router and their features?
Vue Router is a official routing library for single-page applications designed for use with the Vue.js framework.

Below are their features,
1. Nested route/view mapping
2. Modular, component-based router configuration
3. Route params, query, wildcards
4. View transition effects powered by Vue.js' transition system
5. Fine-grained navigation control
6. Links with automatic active CSS classes
7. HTML5 history mode or hash mode, with auto-fallback in IE9
8. Restore scroll position when going back in history mode
