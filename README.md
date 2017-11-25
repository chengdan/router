#路由

##路由的基本使用

    //1. 引入vue-router.js
    //2. 创建组件构造对象
    var login = {
        template: "<h1>login</h1>s"
    }
    //3. 创建vuerouter实例 路由对象
    var router = new VueRouter({
        //4. 在vuerouter对象中 指定路由规则
        routes: [
            {
                //路由路径
                path: "/login",
                component: login
            }
        ]
    })
    
    //5. 将router和vue实例关联起来
    var vm = new Vue({
        router: router
    })
    
    //6. 在视图中指定路由组件显示的位置
    //<router-view></router-view>

##路由参数

1. 通过?传递
    ?key=value&key=value
    获取； this.$route.query
2. 通过路由规则声明
    /login/:id
    /login/12
    获取: this.$route.params

router-link

这个可以代替a标签， 他会自动的将和当前页面的地址匹配的a标签加上 router-link-active的类样式

    <router-link to="/login"></router-link>
    <router-link :to="{path: '/login'}"></router-link>
    <router-link :to="{name: '路由的名字'}"></router-link>

##命名路由
在routes：[]里加上一个name属性即可

```javascript
var router = new VueRouter({
        routes :[
            {
                name : 'home',
                path : '/index/436',
                component :{
                    template : "<h1>首页</h1>"
                }
            },
            {
                name : 'login',
                path : '/login/wqe/234',
                component : {
                    template : "<h1>登录页</h1>"
                }
            },
            {
                name : 'register',
                path : '/register',
                component :{
                    template : "<h1>注册页</h1>"
                }
            }
        ]
    })
    let vm = new Vue({
        router,
        el:'#app',
        data:{

        }
    })
```

##嵌套路由

    var router = new VueRouter({
        routes: [
            {
                path: "/login",
                component: login,
                children: [
                    //一定要在上层路由的组件中，为下层路由匹配的组件指定显示位置
                    //router-view
                    {
                        //子路由中的path不能以/开头
                        path: "xyz",
                        component: xyz,
                    }
                ]
            }
        ]
    })

##编程式导航（通过js代码进行路由跳转）

    this.$router.push("/login")tm


