# QUIZ

## 問題一

> 題目：
>
> ```
> function readData(idx) {
>  for (let i = 0; i < 100; i++) {
>    idx++;
>    console.log(idx);
>  }
>  if (idx < 500) {
>    readData(idx);
>  }
> }
>
> readData(0);
> console.log("after");
> ```
>
> 答案：
>
> ```
> 1
> ~
> 500
> after
> ```

## 問題二

> 題目：
>
> ```
> function readData(idx) {
>  for (let i = 0; i < 100; i++) {
>    idx++;
>    console.log(idx);
>  }
>  if (idx < 500) {
>    setTimeout(function () {
>      readData(idx);
>    }, 0);
>  }
> }
>
> readData(0);
> console.log("after");
> ```
>
> 答案：
>
> ```
> 1
> ~
> 100
> after
> 101
> ~
> 500
> ```
