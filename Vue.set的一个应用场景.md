## Vue.set 使用

#### 更新响应式属性

- 场景：组件中的data中定义一个对象obj: {a: 1}，此时对象的属性a是响应式的。但如果在data的外部有一个变量b，变量b不是响应式的。
把变量b赋值给对象中的属性a, 即obj.a = b，那么此时对象中的a指向了b，属性a不再具有响应式。
如果想把变量b的值赋值给a，还让a具有响应式，就可以用Vue.set()方法。

- 接受三个参数：Vue.set()接受三个参数，第一个是data中的对象，第二个参数是接受赋值的属性名，第三个是要赋的值。上面的例子就可以这么写:

```
Vue.set(vm.obj, a, b)
```

#### 添加响应式属性

- Vue.set 也可以向嵌套对象中添加响应式属性

向嵌套对象userProfile中 添加一个新的age属性
```
Vue.set(this.userProfile, 'age', 33)
```

- 单文件组件中可以这么写
```
vm.$set(vm.userProfile, 'age', 33)
```

#### 为已有对象赋值多个新属性

```
vm.userProfile = Object.assign({}, vm.userProfile, {
  age: 27,
  favoriteColor: 'Vue Green'
})
```