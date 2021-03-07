# 1. JavaScript规定了几种语言类型 
string number boolean undefined null object  Symbol
# 2. JavaScript对象的底层数据结构是什么
object array function


# 3. Symbol类型在实际开发中的应用、可手动实现一个简单的Symbol
Symbol 是完全不一样的东西。一旦创建后就不可更改，不能对它们设置属性（如果在严格模式下尝试这样做，你将得到一个 TypeError）。它们可以作为属性名，这时它们和字符串的属性名没有什么区别。
var a=Symbol("Sdsd");
console.log(a)
# 4. JavaScript中的变量在内存中的具体存储形式
基本数据类型：基本数据类型值指保存在栈内存中的简单数据段。
引用数据类型：引用数据类型值指保存在堆内存中的对象。也就是，变量中保存的实际上的只是一个指针，这个指针指向内存中的另一个位置，该位置保存着对象。访问方式是按引用访问。
堆&栈
两者都是存放临时数据的地方。
栈是先进后出的，就像一个桶，后进去的先出来，它下面本来有的东西要等其他出来之后才能出来。
堆是在程序运行时，而不是在程序编译时，申请某个大小的内存空间。即动态分配内存，对其访问和对一般内存的访问没有区别。对于堆，我们可以随心所欲的进行增加变量和删除变量，不用遵循次序。
栈区（stack） 由编译器自动分配释放 ，存放函数的参数值，局部变量的值等。 
堆区（heap） 一般由程序员分配释放，若程序员不释放，程序结束时可能由OS回收。 
堆（数据结构）：堆可以被看成是一棵树，如：堆排序； 
栈（数据结构）：一种先进后出的数据结构。
# 5. 基本类型对应的内置对象，以及他们之间的装箱拆箱操作

# 6. 理解值类型和引用类型
（1）值类型：1、占用空间固定，保存在栈中（当一个方法执行时，每个方法都会建立自己的内存栈，在这个方法内定义的变量将会逐个放入这块栈内存里，随着方法的执行结束，这个方法的内存栈也将自然销毁了。因此，所有在方法中定义的变量都是放在栈内存中的；栈中存储的是基础变量以及一些对象的引用变量，基础变量的值是存储在栈中，而引用变量存储在栈中的是指向堆中的数组或者对象的地址，这就是为何修改引用类型总会影响到其他指向这个地址的引用变量。）
2、保存与复制的是值本身
3、使用typeof检测数据的类型
4、基本类型数据是值类型
（2）引用类型：1、占用空间不固定，保存在堆中（当我们在程序中创建一个对象时，这个对象将被保存到运行时数据区中，以便反复利用（因为对象的创建成本通常较大），这个运行时数据区就是堆内存。堆内存中的对象不会随方法的结束而销毁，即使方法结束后，这个对象还可能被另一个引用变量所引用（方法的参数传递时很常见），则这个对象依然不会被销毁，只有当一个对象没有任何引用变量引用它时，系统的垃圾回收机制才会在核实的时候回收它。）
2、保存与复制的是指向对象的一个指针
3、使用instanceof检测数据类型
4、使用new()方法构造出的对象是引用型

# 7. null和undefined的区别 
null： Null类型，代表“空值”，代表一个空对象指针，使用typeof运算得到 “object”，所以你可以认为它是一个特殊的对象值。
undefined： Undefined类型，当一个声明了一个变量未初始化时，得到的就是undefined。
# 8.至少可以说出三种判断JavaScript数据类型的方式，以及他们的优缺点，如何准确的判断数组类型
1.typeof 's'    //string
2.[] instanceof Array  //true
3.console.log([].constructor === Array);//->true
# 9.可能发生隐式类型转换的场景以及转换原则，应如何避免或巧妙应用
 1+'1' 

# 10.出现小数精度丢失的原因，JavaScript可以存储的最大数字、最大安全数字，JavaScript处理大数字的方法、避免精度丢失的方法
前端出现问题的几率可能比较低，毕竟很少有业务需要需要用到超大整数，只要运算结果不超过 Math.pow(2, 53) 就不会丢失精度。 

# 11、数组的方法
push() 在最后插入
pop() 删除数组最后一项   
shift() 删除第一个 
unshift() 在数组前插入 
join(',') 将数组转换成字符串加分隔符  
sort() 数组排序  

reverse() 反转数组顺序

concat() 合并数组 原数组不会修改




# 遇到过的bug，如何解决
>1、ios 12.0版本微信端，使用position abosulte 绝对定位时的输入框，失去焦点时，整体页面不会下拉下来，底部会空出一块。
解决办法：封装个指令， 创建个绝对定位的input在顶部，把焦点焦距到该input，使页面整体拉下来，恢复原状，在失去焦点
>2、 iOS高版本中，在微信内访问网页，音频背景音乐无法自动播放
 document.addEventListener('WeixinJSBridgeReady', function() {},false)
 >3、页面上可播放的视频大多需要是mp4格式的，且其格式需是H.264，否则某些情况下会碰到有声音没画面的现象
 >4、数据量大滚动时的卡顿，可以尝试加上will-change: transform来避免重新布局

>5、修改本地时间，调用 new Date() 获取时间会有延迟
修改本地时间后，这个获取时间某些情况下会不正确。原因是浏览器自身缓存了当前时间值。
当修改的时间变化比较小时（比如改变几分钟）能更新到正确的值
改变比较大时（比如改变几十分钟或几天），这个值在一分钟左右才会更新出来

>6、border-radius遇到transform,overflow:hidden失效
解决方案多为 mask-image,
查阅资料后找到另一种方法  transform-style:preserve-3d，父元素同时设置transform: rotate(0deg)；

>7、input[file]标签的accept=”image/*”属性响应很慢的解决办法
<input type="file" accept="image/gif,image/jpeg,image/jpg,image/png,image/svg">
accept=”image/*”属性会对每一个文件都遍历一次所有的”image/*”文件类型，当文件较多时，文件的检验时间较长，这可能是Webkit的底层实现的bug。
另外，
accept=”audio/*”和 accept=”video/*” 属性 在 Webkit浏览器下也会有同样的响应延迟的问题。同理，通过将 * 通配符 修改成指定的MIME类型就可解决。



# 深浅拷贝
>浅拷贝
Object.assign
let a = {
    age: 1
}
let b = Object.assign({}, a)
浅拷贝只解决了第一层的问题，

>深拷贝
let b = JSON.parse(JSON.stringify(a))
但是该方法也是有局限性的：

会忽略 undefined
会忽略 symbol
不能序列化函数
不能解决循环引用的对象




# 排序算法
1、冒泡排序
function bubbleSort(arr){
  var i = j = 0;
  for(i=1; i<arr.length; i++){
    for(j=0; j<=arr.length-i; j++){
      var temp = 0;
      // ">" 从小到大排序
      // "<" 从大到小排序
      if(arr[j] > arr[j+1]){
        temp = arr[j]
        arr[j] = arr[j+1]
        arr[j+1] = temp
      }
    }
  }
  return arr
}
2、快速排序
function quickSort(arr,l,r){
  if(l < r){
    var i = l, j = r, x = arr[i];
    while(i<j){
      while(i<j && arr[j]>x)
        j--;
      
      if(i<j)
        //这里用i++，被换过来的必然比x小，赋值后直接让i自加，不用再比较，可以提高效率
        arr[i++] = arr[j];
      
      while(i<j && arr[i]<x)
        i++;
      
      if(i<j)
        //这里用j--，被换过来的必然比x大，赋值后直接让j自减，不用再比较，可以提高效率
        arr[j--] = arr[i];
    }
    arr[i] = x;
    
    quickSort(arr, l, i-1);
    quickSort(arr, i+1, r);
  }
}
3、二路归并
function merge(left, right) {
    var result = [],
        il = 0,
        ir = 0;

    while (il < left.length && ir < right.length) {
        if (left[il] < right[ir]) {
            result.push(left[il++]);
        } else {
            result.push(right[ir++]);
        }
    }
    while(left[il]){
        result.push(left[il++]);
    }
    while(right[ir]){
        result.push(right[ir++]);
    }
    return result;
}
字符串操作
1、判断回文字符串
function palindrome(str){
  // \W匹配任何非单词字符。等价于“[^A-Za-z0-9_]”。
  var re = /[\W_]/g;
  // 将字符串变成小写字符,并干掉除字母数字外的字符
  var lowRegStr = str.toLowerCase().replace(re,'');
  // 如果字符串lowRegStr的length长度为0时，字符串即是palindrome
  if(lowRegStr.length===0) return true;
  // 如果字符串的第一个和最后一个字符不相同，那么字符串就不是palindrome
  if(lowRegStr[0]!=lowRegStr[lowRegStr.length-1]) return false;
  //递归
  return palindrome(lowRegStr.slice(1,lowRegStr.length-1));
}
2、翻转字符串
思路一：反向遍历字符串
function reverseString(str){
  var tmp = '';
  for(var i=str.length-1; i>=0; i--)
    tmp += str[i];
  return tmp
}
思路二：转化成array操作
function reverseString(str){
  var arr = str.split("");
  var i = 0,j = arr.length-1;
  while(i<j){
    tmp = arr[i];
    arr[i] = arr[j];
    arr[j] = tmp;
    i++;
    j--;
  }
  return arr.join("");
}
3、生成指定长度随机字符串
function randomString(n){
  var str = 'abcdefghijklmnopqrstuvwxyz0123456789';
  var tmp = '';
  for(var i=0; i<n; i++) {
    tmp += str.charAt(Math.round(Math.random()*str.length));
  }
  return tmp;
}
4、统计字符串中次数最多字母
function findMaxDuplicateChar(str) {
  if(str.length == 1) {
    return str;
  }
  var charObj = {};
  for(var i = 0; i < str.length; i++) {
    if(!charObj[str.charAt(i)]) {
      charObj[str.charAt(i)] = 1;
    } else {
      charObj[str.charAt(i)] += 1;
    }
  }
  var maxChar = '',
      maxValue = 1;
  for(var k in charObj) {
    if(charObj[k] >= maxValue) {
      maxChar = k;
      maxValue = charObj[k];
    }
  }
  return maxChar + '：' + maxValue;
}
数组操作
1、数组去重
function unique(arr){
  var obj = {}
  var result = []
  for(var i in arr){
    if(!obj[arr[i]]){
      obj[arr[i]] = true;
      result.push(arr[i]);
    }
  }
  return result;
}
2、数组中最大差值
function getMaxProfit(arr){
  var min = arr[0],
      max = arr[0];
  for(var i = 0; i < arr.length; i++){
    if(arr[i] < min) min = arr[i];
    if(arr[i] > max) max = arr[i];
  }
  return max - min;
}
其他常见算法
1、阶乘
非递归实现
function factorialize(num) {
  var result = 1;
    if(num < 0) return -1;
    if(num == 0 || num == 1) return 1;
    while(num>1) {
      result *= num--;
    }
    return result;
}
递归实现
function factorialize(num) {
  var result = 1;
  if(num < 0) return -1;
  if(num == 0 || num == 1) return 1;
  if(num > 1) return num*factorialize(num-1);
}
2、生成菲波那切数列
强行递归实现
function getfib(n){
  if(n == 0) return 0;
  if(n == 1) return 1;
  if(n > 1) return getfib(n-1) + getfib(n-2);
}
function fibo(len){
    var fibo = [];
    for(var i = 0; i < len; i++){
      fibo.push(getfib(i));
    }
    return fibo;
}
简约非递归实现
function getFibonacci(n) {
  var fibarr = [];
  var i = 0;
  while(i < n) {
    if(i <= 1) {
      fibarr.push(i);
    } else {
      fibarr.push(fibarr[i - 1] + fibarr[i - 2])
    }
    i++;
  }
  return fibarr;
}
3、二分查找
非递归实现
function binary_search(arr, key) {
  var low = 0,
      high = arr.length - 1;
  while(low <= high){
    var mid = parseInt((high + low) / 2);
    if(key == arr[mid]){
      return mid;
    }else if(key > arr[mid]){
      low = mid + 1;
    }else if(key < arr[mid]){
      high = mid -1;
    }
  }
  return -1;
}
递归实现
function binary_search2(arr, low, high, key) {
  if(low > high) return -1;
  var mid = parseInt((low + high)/2);
  if(key == arr[mid]) {
    return mid;
  } else if(key > arr[mid]) {
    return binary_search2(arr, mid+1, high, key);
  } else if(key < arr[mid]) {
    return binary_search2(arr, low, mid-1, key);
  }
}
