## Разработка приложения для асинхронного считывания данных из JSON и вывода в веб-документ путём нативной модификации дерева DOM

Данные JSON получены по адресу https://kodaktor.ru/j/users.

Данные считываются с помощью fetch. Модификация дерева DOM происходит путём вызова функции appendChild.

Скриншот приложения:  
![Скриншот приложения](/screenshots/task.png)
<html>
    <head>
        <meta charset="utf-8">
    </head>
    <body>
        <button id="btn">Get Data</button>
        <div id="data">
            <ul id="users"></ul>
        </div>
        <script>
            document.querySelector('#btn').onclick = async () => {
                let response = await fetch('https://kodaktor.ru/j/users');
                data = await response.json();
                data.users.forEach(user => {
                    let ul = document.querySelector('#users');
                    let li = document.createElement('li');
                    li.appendChild(document.createTextNode(user.login));
                    ul.appendChild(li);
                });
            }
        </script>
    </body>
</html>

Код приложения (фрагмент script):

```js
document.querySelector('#btn').onclick = async () => {
    let response = await fetch('https://kodaktor.ru/j/users');
    data = await response.json();
    data.users.forEach(user => {
        let ul = document.querySelector('#users');
        let li = document.createElement('li');
        li.appendChild(document.createTextNode(user.login));
        ul.appendChild(li);
    });
}
```
