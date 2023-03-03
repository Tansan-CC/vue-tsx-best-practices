# Vue 中使用 TSX 的方式

## 组件的定义方式

### 1. 无参数并且无状态组件

_src/example/TSX.vue_
我们可以用纯函数的方式进行定义, 此函数可以简单的理解成一段静态的 TSX 代码。

### 2. 有参数并且无状态的组件

_src/example/TSXControllable.vue_
依旧可以使用纯函数进行定义。 每当参数变化时, 会重新渲染组件(重新运行函数)。

### 3. 无参数并且有状态的组件

_src/example/TSXEffect.vue_
这种情况下不可以使用纯函数的方式定义, 可以使用 `defineComponent` API。此 API 的其中一个重载只需要一个 `setup` 函数作为参数, 该函数会在组件初始化时执行, 并且返回一个**返回值为 TSX 的函数**。每当状态发生变化时, 会重新运行返回的函数进行重新渲染。

### 4. 有参数并且有状态的组件

_src/example/TSXControllableEffect.vue_
与上一条相同, 依旧使用`defineComponent` API 参数的定义可以使用泛型来进行定义。但是一定要在定义完之后使用 Component.props = [propName]的方式重新告诉 vue 此组件有哪些参数。

## 总结

界定是否使用`defineComponent`, 需要看组件是否有状态, 有状态的组件必须使用`defineComponent` API。
因为 vue 的参数声明必需是运行时的, 因此在有状态且有参数的组件中, 必需再声明后重新赋值给`Component.props`。希望 vue 的后续更新可以解决这个问题。

## 勘误

发现问题或有修改建议请提出 PR 或者 issue, 我会及时响应。感谢你的协助 🙏。
