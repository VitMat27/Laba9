# Laba9

<p align = "center">МИНИСТЕРСТВО НАУКИ И ВЫСШЕГО ОБРАЗОВАНИЯ<br>
РОССИЙСКОЙ ФЕДЕРАЦИИ<br>
ФЕДЕРАЛЬНОЕ ГОСУДАРСТВЕННОЕ БЮДЖЕТНОЕ<br>
ОБРАЗОВАТЕЛЬНОЕ УЧРЕЖДЕНИЕ ВЫСШЕГО ОБРАЗОВАНИЯ<br>
«САХАЛИНСКИЙ ГОСУДАРСТВЕННЫЙ УНИВЕРСИТЕТ»</p>
<br><br><br><br><br><br>
<p align = "center">Институт естественных наук и техносферной безопасности<br>Кафедра информатики<br>Иванюшин Виталий Петрович</p>
<br><br><br>
<p align = "center"><br><strong>Лабораторная работа №9.«JS»</strong><br>01.03.02 Прикладная математика и информатика</p>
<br><br><br><br><br><br><br><br><br><br><br><br>
<p align = "right">Научный руководитель<br>
Соболев Евгений Игоревич</p>
<br><br><br>
<p align = "center">г. Южно-Сахалинск<br>2024 г.</p>
<br><br><br><br><br><br><br><br><br><br><br><br>

<h1 align = "center">Введение</h1>

<p><b>HTML</b> —  стандартизированный язык гипертекстовой разметки документов для просмотра веб-страниц в браузере. Веб-браузеры получают HTML документ от сервера по протоколам HTTP/HTTPS или открывают с локального диска, далее интерпретируют код в интерфейс, который будет отображаться на экране монитора.</p>
<p><b>CSS</b> — формальный язык описания внешнего вида документа, написанного с использованием языка разметки. Также может применяться к любым XML-документам, например, к SVG или XUL.</p>


<h1 style="text-align: center">Задачи js</h1>
<ol> <li>Есть некоторая строка (var str = 'fgfggg';), что будет, если мы возьмем str[0]?</li> <li>Дана функция, она принимает в качестве аргументов строки '*', '1', 'b', '1c', реализуйте ее так, что бы она вернула строку '1*b*1c'</li> <li>Дано дерево, надо найти сумму всех вершин.</li> <li>Нарисовать стилями полукруг.</li> <li>Есть массив в котором лежат объекты с датами, отсортировать по датам.</li> <li>Есть несколько слов, определить состоят ли они из одних и тех же букв('кот', 'ток', 'окт')</li> <li>От них же. Числа от 1 до 100 лежат в массиве, они хаотично перемешанные, от туда изъяли одно число, надо найти, что это за число. алгоритм не должен превышать O(n^2) сложности.</li> <li>Реализовать сортировку пузырьком.</li> <li>Обратная польская нотация.</li> <li>Реализовать функцию является ли слово палендром.</li> </ol>



<h1 style="text-align: center">Решения</h1>



```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>


    <script>
        //1
        var str = 'fgfggg';
        console.log(str[0]); // Вернет символ 'f'


        //2
                function concatenateStrings(...args) {
            return args.filter(arg => typeof arg === 'string').join('*');
        }

        console.log(concatenateStrings('*', '1', 'b', '1c')); // Вернет '1*b*1c'

            //3
// Предположим, что дерево представлено в виде массива nodes, где каждый элемент - это вершина дерева
function sumTreeNodes(nodes) {
    let sum = 0;
    nodes.forEach(node => sum += node.value);
    return sum;
}
            
     


            //5
const datesArray = [
    { date: new Date('2022-01-15') },
    { date: new Date('2022-03-10') },
    { date: new Date('2022-02-05') }
];

datesArray.sort((a, b) => a.date - b.date);
            //6
            function areAnagrams(...words) {
    const sortedWords = words.map(word => word.split('').sort().join(''));
    return new Set(sortedWords).size === 1;
}

console.log(areAnagrams('кот', 'ток', 'окт')); // Вернет true
            //7
            const numbersArray = [1, 3, 2, 5, 4]; // Пример массива чисел
const missingNumber = numbersArray.length * (numbersArray.length + 1) / 2 - numbersArray.reduce((sum, num) => sum + num, 0);
            //8
            function bubbleSort(arr) {
    for (let i = 0; i < arr.length; i++) {
        for (let j = 0; j < arr.length - 1 - i; j++) {
            if (arr[j] > arr[j + 1]) {
                [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
            }
        }
    }
    return arr;
}
            //9
            function evaluateReversePolishNotation(tokens) {
    const stack = [];
    const operators = ['+', '-', '*', '/'];

    tokens.forEach(token => {
        if (!operators.includes(token)) {
            stack.push(parseInt(token));
        } else {
            const b = stack.pop();
            const a = stack.pop();
            switch (token) {
                case '+':
                    stack.push(a + b);
                    break;
                case '-':
                    stack.push(a - b);
                    break;
                case '*':
                    stack.push(a * b);
                    break;
                case '/':
                    stack.push(Math.trunc(a / b));
                    break;
            }
        }
    });

    return stack.pop();
}
            //10
            function isPalindrome(word) {
    return word === word.split('').reverse().join('');
}

console.log(isPalindrome('radar')); // Вернет true
        
    </script>
</body>
</html>




<!DOCTYPE html>
<html>
<head>
    <title>Полукруг</title>
    <style>
        .semicircle {
            width: 200px;
            height: 100px;
            background-color: #4CAF50;
            border-radius: 100px 100px 0 0;
        }
    </style>
</head>
<body>
<div class="semicircle"></div>
</body>
</html>
```



<h1 align = "center">Вывод</h1>
<p>В ходе выполнения лабораторной работы по js были рассмотрены различные селекторы, которые позволяют выбирать и стилизовать определенные элементы на веб-странице. 
