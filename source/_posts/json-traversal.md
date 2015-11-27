title: JSON 遍历
date: 2014-09-19 19:06:11
tags:
    - json
    - array
categories: Front-End
---
### grep

``` javascript
var array = [1, 2, 3, 4, 5, 6, 7, 8, 9];
var filterArray = $.grep( array, function( value ) {
    return value > 5;   // 筛选出大于 5 的
});

for( var i = 0; i < filterArray.length; i++ ) {
    alert( filterArray[i] );
}

for ( key in filterArray ) {
    alert( filterArray[key] );
}
```

### each

<!--more-->

``` javascript
var anObject = {one : 1, two : 2, three : 3};    // 对 json 数组 each
$.each( anObject, function( name, value ) {
    alert( name );
    alert( value );
});

var anArray = ['one', 'two', 'three'];
$.each (anArray, function( n, value ) {
    alert( n );
    alert( value );
});
```

### inArray

``` javascript
var anArray = ['one', 'two', 'three'];
var index = $.inArray( 'two', anArray );
alert( index );    // 返回该值在数组中的键值，返回 1
alert( anArray[index] );    // value is two
```

### map

``` javascript
var strings = ['0', '1', '2', '3', '4', 'S', '6'];
var values = $.map( strings, function( value ) {
    var result = new Number( value );
    return isNaN( result ) ? null : result;    // isNaN: is Not a Number 的缩写
});

for ( key in values ) {
    alert( values[key] );
}
```

### JSON 对象

``` javascript
var json = [{ dd : 'SB', AA : '东东', re1 : 123 }, { cccc : 'dd', lk : '1qw' }];
for( var i = 0, l = json.length; i < l; i++ ) {
    for( var key in json[i] ){
        alert( key + ':' + json[i][key] );
    }
}
```

``` javascript
var obj = { "name" : "冯娟", "password" : "123456", "department" : "技术部", "sex" : "女", "old" : 30 };
for( var p in obj ) {
    str = str + obj[p] + ',';
    return str;
}
```
