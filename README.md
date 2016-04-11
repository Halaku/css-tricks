# Размер правой части зависит от левой
```
.left-part {
  float: left
}
.right-part {
  overflow: hidden
}
```

# Центрование
### Ячейка таблицы
Только для фиксированных размеров обертки внутри контейнера
```
.container {
  width:200px;
  height:200px;
  .wrap {
  display: table-cell;
  width:200px;
  height:200px;
  text-align: center;
  vertical-align: middle;
   & img {
     display: inline-block;
   }
  }
}
```
### Через absolute и margin: auto
Должны быть заданы размеры контейнера и их можно менять (можно в %)
```
.container {
  width:200px;
  height:200px;
  position: relative;
  & img {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    margin: auto;
    display: block;
  }
}
```
### Через absolute и 50%
Должны быть известны размера центрируемого контента
```
.container {
  position: relative;
  img {
    display: block;
    position: absolute;
    top: 50%;
    left: 50%;
    margin-top: -75px;
    margin-left: -75px;
  }
}
```
### Через transform
Только для новых браузеров (ie10+) http://caniuse.com/#search=transform
```
.container {
  position: relative;
  img {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translateX(-50%) translateY(-50%);
  }
}
```

### Фокус с дополнительны нулевым элементом
Для старых бразуеров, хорошо заходит для попапа авторизации
```
.auth-wrapper {
  min-width: 300px; // Значение  равно ширине auth-form, иначе баг при ширине окна меньше, чем ширина auth-form
  position: absolute;
  top: 0:
  bottom: 0; // Это считается жестко заданными размерами
  left: 0; // нужно для фокуса с дополнительный элементом с height: 100%
  right: 0;
  text-align: center; // Для горизонтального овыравнивания окна авторизации
  &:before {
    contant: '';
    display: inline-block;
    height: 100%;
    width: 0;
    vertical-align: middle; // выравнивает инлайновые элементы по вертикали
  }
}

.auth-form {
  display: inline-block;
  vertical-align: middle;
}
```
### Через line-height
Чаще всего для кнопок, только для однострочных
```
.button {
  width: 100px;
  height: 50px;
  line-height: 50px; // Равна высоте блока
  text-align: center;
}
```

# Растягиваем содержимое navbar
```
.nav-list {
  text-align: justify;
  &:after {
    content: ''; // justify работает только для многострочного контента
    display: inline-block; // after как раз добавляет вторую строку
    width: 100%; // которая займет 100% ширины
    height: 0;
  }
}

.nav-item {
  display: inline-block;
}
```
