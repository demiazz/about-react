# Кратко о React

[Алексей Плуталов](https://twitter.com/demiazz), [Злые марсиане](http://evilmartians.ru/)

## **Кратко о React**
!type is-title

*Алексей Плуталов, Злые марсиане*

!image martian.png

## План

1. Шаблонизация: вчера и сегодня
2. React is...
3. FLUX
4. Вопросы
5. Рекламная пауза

## *Часть 1* Шаблонизация: <br /> вчера и сегодня
!type shout

!image martian.png

## *Шаблонизация: вчера и сегодня* Реалии прошлых дней
!type is-default

- статичные страницы
- мало контента
- мало интерактива
- медленный JavaScript

## *Шаблонизация: вчера и сегодня* Решения прошлых дней
!type is-default

- основной рендеринг на клиенте
- небольшое оживление страницы на клиенте
- иногда генерация HTML конкатенацией строк

## *Шаблонизация: вчера и сегодня* Пример ручной шаблонизации
!type is-default
!type with-small-code

```javascript
$(function ($) {
  var notify = function (msg, type) {
    var html;

    html = "<div class='ntf ntf-" + type + "'>" + message + "</div>";

    $("body").append(html);
  };

  window.notify = notify;
})(jQuery);
```

## *Шаблонизация: вчера и сегодня* Реалии недавнего прошлого
!type is-default

- динамичные страницы
- много контента
- много интерактива
- быстрый JavaScript
- SPA

## *Шаблонизация: вчера и сегодня* Решения недавнего прошлого
!type is-default

- явление DHTML
- DOM-библиотеки (mootools, prototype, jQuery)
- фреймворки (Backbone, Knockout, Dojo, SproutCore, ExtJS)
- строковые шаблонизаторы (mustache, ejs, jade)

## *Шаблонизация: вчера и сегодня* Пример строкового шаблона
!type is-default
!type with-small-code

```mustache
<head>
  <title>
    {{ title }}
  </title>
</head>
```

```javascript
function (title) {
  return "<head><title>" + title + "</title></head>";
}
```

## *Шаблонизация: вчера и сегодня* Структура строкового шаблона
!type is-default

- строки
- инструкции (код, условия, циклы и т. д.)

## *Шаблонизация: вчера и сегодня* Особенности шаблона
!type is-default

- неструктурированная строка
- непредсказуемые трансформации строки в будущем
- универсальность

**Итог:** неизвестность структуры и трансформаций конечного DOM

## *Шаблонизация: вчера и сегодня* Создание фрагмента DOM
!type is-default

1. генерация строки
2. сборка DOM (innerHTML/innerSVG)
3. пост-обработка

## *Шаблонизация: вчера и сегодня* Сборка DOM
!type is-default

1. парсинг строки
2. конструирование DOM
3. вставка и ререндер страницы

## *Шаблонизация: вчера и сегодня* Пост-обработка
!type is-default

1. получить ссылки на элементы
2. привязка событий
3. выполнение дополнительного обслуживающего кода

Как правило, этот этап является бутылочным горлышком.

## *Шаблонизация: вчера и сегодня* Модификация фрагмента DOM
!type is-default

1. генерация строки
2. сборка DOM (innerHTML/innerSVG)
3. пост-обработка

Одни и те же медленные процессы.

## *Шаблонизация: вчера и сегодня* Реалии настоящего дня
!type is-default

- еще более динамичные страницы
- еще больше данных
- еще больше интерактива
- еще больше вычислений
- еще больше размер клиентских приложений

## *Шаблонизация: вчера и сегодня* Решения настоящего дня
!type is-default

- двусторонний биндинг
- расцвет MV* фреймворков
- DOM-шаблонизация
- функциональное и реактивное программирование
- концепции веб-компонентов

## *Шаблонизация: вчера и сегодня* Пример DOM шаблона
!type is-default

```jsx
/** @jsx React.DOM */
<h1 className="user-name">
  User:
  <span className="user-name__cnt">
    { userName }
  </span>
</h1>
```

## *Шаблонизация: вчера и сегодня* Структура DOM шаблона
!type is-default

- DOM узлы
- инструкции (код, условия, циклы и т. д.)

DOM узлы связываются в единое DOM-дерево.

## *Шаблонизация: вчера и сегодня* Особенности DOM-шаблона
!type is-default

- структурированная строка
- предсказуемые трансформации DOM в будущем
- заточенность под HTML
- может иметь некоторые ограничения

**Итог:** детерминированность структуры и трансформаций.

## *Шаблонизация: вчера и сегодня* Создание и модификация
!type is-default

Создание фрагмента DOM:

- парсинг шаблона (если нужно), анализ
- создание фрагмента DOM
- операции над DOM и пост-обработка

Модификация производится путем DOM-операций.

## *Шаблонизация: вчера и сегодня* Возможные оптимизации
!type is-default

- легкая версия DOM
- синхронизация изменений наборами
- обновление DOM по [requestAnimationFrame]
- внутренние события, вместо DOM
- использование оптимальных путей обновления DOM
- ручной контроль обновлений
- упрощение привязки данных и событий

[requestAnimationFrame]: https://developer.mozilla.org/ru/docs/DOM/window.requestAnimationFrame

## *Часть 2* React is...
!type shout

!image martian.png

## *React is...* Описание
!type is-default

- не фреймворк
- DOM-шаблонизатор
- библиотека компонент

Библиотека для разработки пользовательского интерфейса

## *React is...* Основные концепции
!type is-default

- разделение UI на дерево компонентов
- использование DOM шаблонизации
- однонаправленный поток данных

## *React is...* Компонент
!type is-default

- шаблон (комбинация нативного и виртуального DOM)
- свойства и состояние
- жизненный цикл
- конечный автомат

## *React is...* Пример компонента
!type is-default
!type with-small-code

```javascript_jsx
/** @jsx React.DOM */

var Greeting = React.createClass({
  render: function () {
    return <div>Привет, { this.props.welcomed }!</div>;
  }
});

React.render(<Greeting welcomed="коллеги" />, document.body);
```

## *React is...* JSXTransform
!type is-default

- не шаблонизатор
- визуализация структуры HTML
- простые преобразования
- трансформация HTML в дерево вызовов JS
- нет накладных расходов

## *React is...* Пример трансформации
!type is-default

```javascript_jsx
<div>
  Привет, { this.props.welcomed }!
</div>
```

```javascript
React.createElement(
  "div", null, "Привет, ",  this.props.welcomed, "!"
)
```

## *React is...* Свойства (Properties)
!type is-default

- данные компонента
- меняются извне
- доступна валидация
- достоверный источник данных

## *React is...* API свойств
!type is-default

- `this.props`
- `this.propTypes`
- `this.getDefaultProps`
- `this.setProps`
- `this.replaceProps`

## *React is...* Состояние (State)
!type is-default

Данные влияющие на внешний вид компонента.

- события
- изменение состояния
- обновление внешнего вида компонента

## *React is...* Рекомендации
!type is-default

- в идеале не должны использоваться
- это не computed properties
- нельзя класть компоненты в состояние
- не должны дублировать данные свойств

## *React is...* API состояния
!type is-default

- `this.state`
- `this.getInitialState`
- `this.setState`
- `this.replaceState`

## *React is...* Жизненный цикл
!type is-default

- монтирование
- обновление
- размонтирование

## *React is...* Монтирование элемента
!type is-default

- `this.getDefaultProps`
- `this.getInitialState`
- `this.componentWillMount`
- `this.componentDidMount`

## *React is...* Обновление элемента
!type is-default

- `this.componentWillReceiveProps`
- `this.shouldComponentUpdate`
- `this.componentWillUpdate`
- `this.componentDidUpdate`

## *React is...* Размонтирование элемента
!type is-default

- `this.componentDidUnmount`

## *React is...* Рендеринг
!type is-default

- `this.render`
- должен возвращать React компонент, `null` или `false`
- должен возвращать только одну ноду
- нельзя менять состояние компонента
- содержит вычисления, нужные для рендеринга
- нельзя добавлять логику работы с браузером

## *React is...* Взаимодействие с браузером
!type is-default
!type with-smallest-code

```javascript_jsx
var LoginForm = React.createClass({
  componentDidMount: function () {
    if (this.props.email.length === 0) {
      this.refs.email.getDOMNode().focus();
    } else {
      this.refs.password.getDOMNode().focus();
    }
  },
  render: function () {
    return (<form>
      <input type="text" ref="email" value={ this.props.email } />
      <input type="password" ref="password" value="" />
    </form>);
  }
});
```

## *React is...* Пример обработки событий
!type is-default
!type with-small-code

```javascript_jsx
var Clicker = React.createClass({
  getInitialState: function () {
    return { count: 0 };
  },
  handleClick: function (e) {
    e.preventDefault();
    this.setState({ count: this.state.count + 1 });
  },
  render: function () {
    return <button onClick={ this.handleClick }>{ this.state.count } />
  }
});
```

## Вот и весь React
!type shout
!type is-centered

## *Часть 3* Flux
!type shout

!type martian.png

## *Flux* Диаграмма взаимодействия
!type with-diagram

!image flux-diagram.png

## Полезное

- Роман Дворнов (Avito): ["Как построить DOM"](http://www.slideshare.net/basisjs/dom-27356908)
- Страница [React](http://facebook.github.io/react/index.html)
- Страница [Flux](http://facebook.github.io/flux/docs/overview.html)
- [ractive](http://www.ractivejs.org/) и [basis.js](http://basisjs.com/)
- [Fluxxor](http://fluxxor.com/), [Reflux](https://github.com/spoike/refluxjs) и [DeLorean](https://github.com/deloreanjs/delorean)

## Вопросы
!type with-em

- Презентация: [demiazz.github.io/about-react](http://demiazz.github.io/about-react/)
- [@demiazz](https://twitter.com/demiazz)

!image evilmartians.png

## На правах рекламы
!type shout

!image martian.png

##
!type evil-icons

<p class="logo">
!image evil-icons.png
</p>

<h3 class="subtitle">Lightweight SVG icons for your web project</h3>

<p class="link"><a href="http://evil-icons.io/">evil-icons.io</a></p>
