# Deferred

# API

### deferred.done

当deferred.resolve被触发的时候,就会通知注册在done里面的事件触发

`deferred.done( doneCallbacks [, doneCallbacks ] )`

## deferred.fail

当deferred.reject被触发的时候,就会通知注册在done里面的事件触发

`deferred.fail( failCallbacks [, failCallbacks ] )`

## deferred.progress

添加消息回调函数

`deferred.progress( progressCallbacks [, progressCallbacks ] )`

## deferred.then

同时添加到成功回调,失败回调,消息回调函数

deferred.then( doneFilter [, failFilter ] [, progressFilter ] )

## deferred.always

添加回调函数,当异步队列处于成功或失败状态时被调用

deferred.always( alwaysCallbacks [, alwaysCallbacks ] )

## deferred.resolve

使用指定的参数调用所有成功回调函数,异步队列进入成功状态

`deferred.resolve( [args ] )`

类似的`deferred.resolveWith( context [, args ] )`

## deferred.reject

使用指定的参数调用所有失败回调函数,异步队列进入失败状态

`deferred.reject( [args] )`

类似的`deferred.rejectWith( context [, args ] )`

## deferred.notify

使用指定的参数调用消息回调函数

`deferred.notify ( [args] )`

类似的`deferred.notifyWith( context, [args] )`

## deferred.state

判断异步队列当前的状态

`deferred.state()`

## deferred.catch

`注意: 在jquery3.0版本才引入该api`

deferred.catch( fn )的作用和deferred.then(nulll, fn)作用一样

example

```javascript
$.get( "test.php" )
  .then( function() {
    alert( "$.get succeeded" );
  } )
  .catch( function() {
    alert( "$.get failed!" );
  } );
```

## deferred.pipe

`不建议使用`

提供链式使用或过滤一下函数

`deferred.pipe( [doneFilter ] [, failFilter ] [, progressFilter ] )`

过滤的demo

```javascript
var defer = $.Deferred(),
  filtered = defer.pipe(function( value ) {
    return value * 2;
  });
 
defer.resolve( 5 );
filtered.done(function( value ) {
  alert( "Value is ( 2*5 = ) 10: " + value );
});
```

## deferred.promise

返回当前Deferred对象的只读副本,或者为普通对象增加异步队列的功能

# 结构

```javascript
jQuery.exted({
    Deferred: function( func ) {
        var tuples = [
            	[ "notify", "progress", jQuery.Callbacks( "memory" ),
					jQuery.Callbacks( "memory" ), 2 ], //通知回调列表
				[ "resolve", "done", jQuery.Callbacks( "once memory" ),
					jQuery.Callbacks( "once memory" ), 0, "resolved" ], //成功回调列表
				[ "reject", "fail", jQuery.Callbacks( "once memory" ),
					jQuery.Callbacks( "once memory" ), 1, "rejected" ] // 失败回调列表
        ],
            state = 'pending',//初始化为 待定状态
            deferred = {},//
            promise = {
               state(),//返回当前state
               always(),//
            },
        jQuery.each( tuples, function( i, tuple ) {
            
        });
    }
})
```

# 疑问

## tuples的定义
