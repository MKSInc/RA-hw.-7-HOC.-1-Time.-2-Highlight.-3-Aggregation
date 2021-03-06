<a name="top"></a>
[![Build status](https://ci.appveyor.com/api/projects/status/m9ff0es86fssic21?svg=true)](https://ci.appveyor.com/project/MKSInc/ra-hw-7-hoc-1-time-2-highlight-3-aggregation)
### [Gh-pages](https://mksinc.github.io/RA-hw.-7-HOC.-1-Time.-2-Highlight.-3-Aggregation/)

# 7. Домашнее задание к лекции «HOC»

**Перейти к:**  
***[7.2 Популярное и новое](#7.2)  
[7.3 Агрегация данных*](#7.3)***

## 7.1 Форматирование даты публикации

Есть страница, содержащая список видеозаписей. 
У каждого блока есть дата публикации. 

![Relative Time](./assets/time.png)

В данный момент выводится просто текущее значение (Пример `2017-09-01 14:15:10`). 
Было вынесено решение изменять представление даты следующим образом в зависимости от его значения:
`12 минут назад` если прошло меньше часа, `5 часов назад` если прошло больше часа, `X дней назад` если больше суток.

### Реализация

Используя HOC обернуть `DateTime` в компонент `DateTimePretty`, так, чтобы он преобразовывал дату к нужному виду.

Воспользуйтесь готовым файлом `App.js` и стилями `css/index.css` из данного каталога в качестве отправной точки (замените ими те, что создаются в create-react-app).

Для работы с датой и временем можете воспользоваться библиотекой momentjs.


## <a name="7.2">7.2 Популярное и новое</a>
***[(наверх)](#top)***

На нашем сайте есть блоки со статьями и с видео записями. 

![Highlight](./assets/highlight.png)

Мы решили улучшить отображение наших блоков таким образом, 
чтобы популярные статьи и видео (1000+ прочтений/просмотров) 
оборачивались в компонент `Popular`, а с количеством до 
100 в компонент `New`. Эти компоненты будут менять внешний 
облик блоков привлекая внимание посетителей.

### Реализация

Используя HOC обернуть `Video` и `Article` таким образом, чтобы при отображении в компоненте `List` они помещались внутрь требуемого компонента `Popular` или `New`.

Воспользуйтесь готовым файлом `App.js` и стилями `css/index.css` из данного каталога в качестве отправной точки (замените ими те, что создаются в create-react-app).


## <a name="7.3">7.3 Агрегация данных*</a>
***[(наверх)](#top)***

Есть набор из трех компонентов, которые выводят табличные данные: 
- с группировкой по месяцам за текущий год, 
- с группировкой по годам 
- с сортировкой по убыванию. 

![Aggregation](./assets/aggregation.png)

К сожалению, эти компоненты работают только с подготовленными данными, а API сервера статистики возвращает нам «сырые» данные (неотсортированные и несгруппированные).

Данные запрашиваются один раз (https://raw.githubusercontent.com/netology-code/ra16-homeworks/master/hoc/aggregation/data/data.json) – после загрузки страницы.
```js
{
  "list": [
    {"date": "2018-01-13", "amount": 10},
    {"date": "2018-02-13", "amount": 9},
    {"date": "2018-01-09", "amount": 5},
    {"date": "2017-12-14", "amount": 14},
    {"date": "2018-03-01", "amount": 13},
    //...
  ]
}
```

### Реализация

Обернуть компоненты таблиц в HOC, который бы производил над данными операции, приводящие их к нужному виду.
Так же данные, которые группируются по дате, должны быть отсортированы по ней.

Компонент `MonthTable` ожидает данные в свойство `list` в следующем формате 
```js
[{month: "Jan", amount: 100}, ...]
```

Компонент `YearTable` ожидает данные в свойство `list` в следующем формате 
```js
[{year: 2018, amount: 100}, ...]
```

Компонент `SortTable` ожидает данные в свойство `list` в следующем формате 
```js
[{date: "2017-12-14", amount: 14}, ...]
```

Воспользуйтесь готовым файлом `App.js` и стилями `css/index.css` из данного каталога в качестве отправной точки (замените ими те, что создаются в create-react-app).
