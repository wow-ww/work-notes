- 场景描述：页面1中按钮A，点击后跳转页面2；快速多次点击按钮A，会出现跳转到了页面2后，在页面2中，又重复跳转到页面2。
``` js
// 防抖  
let t = null;  
export const debounce = function( fn, delay ) {  
    if( t !== null ) {  
        clearTimeout(t);  
    }  
    t = setTimeout(() => {  
        fn()  
    },delay)  
}

// //调用  
// debounce(() =>{  
//     console.log("内容")  
// },600)
```