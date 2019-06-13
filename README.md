# vue分析

```javascript
  function Vue(options) {
    // 这里是入口
    if (!(this instanceof Vue)
    ) {
      warn('必须用new');
    }
    this._init(options);
  }

  initMixin(Vue);
  stateMixin(Vue);
  eventsMixin(Vue);
  lifecycleMixin(Vue);
  renderMixin(Vue);
```

1. initMixin 中挂载 `_init` 方法搭配vue原型上
    ##### `_init`
      1. initLifecycle
      2. initEvents
      3. initRender
      4. 调用钩子函数 `brforeCreate`
      5. initInjections
      6. initState
      7. initProvide
      8. 调用钩子函数 `created`
      9. 调用钩子函数 `beforeMount`
      10. new 一个 Watcher，并绑定钩子函数 'beforeUpdate'
      11. 调用钩子函数 'mounted'
2. stateMixin 中对 Vue原型 做的事情
    1. 定义`data`和`props`的get、set
    2. 定义vue上的set、del
    3. 定义$watch
3. eventsMixin 中对 Vue原型 做的事情
    1. 事件监听相关内容，待完善
4. lifecycleMixin 中对 Vue原型 做的事情
    1. 定义`_update`更新方法
    2. 定义`$forceUpdate` 强制更新方法
    3. 定义`$destroy`销毁方法
5. renderMixin 中对 Vue原型 做的事情
    1. 定义installRenderHelpers，运行时帮助方法
    2. 绑定 `$nextTick` 方法
    3. 绑定 `_render` 方法
6. 