#  Day 08 - Frontend boot camp

## Contents

1. [Chapter I](#chapter-i) \
   1.1. [Context](#context) \
   1.2 [LocalStorage и SessionStorage](#localstorage-и-sessionstorage) \
   1.3 [Redux](#redux) 

## Chapter I

В этой главе мы рассмотрим как можно избежать так называемого "Props Drilling" и узнаем как и где можно хранить состояние нашего приложения.
  
### Context

[React Context API](https://ru.reactjs.org/docs/hooks-reference.html#usecontext) — это инструмент управления состоянием, используемый для обмена данными между компонентами React. Контекст позволяет передавать данные через дерево компонентов без необходимости передавать пропсы на промежуточных уровнях.
Контекст разработан для передачи данных, которые можно назвать «глобальными» для всего дерева React-компонентов (например, текущий аутентифицированный пользователь, UI-тема или выбранный язык).
[Ключевые моменты](./materials/Context.md)

### LocalStorage и SessionStorage

Объекты веб-хранилища localStorage и sessionStorage позволяют хранить пары ключ/значение в браузере.
Что в них важно – данные, которые в них записаны, сохраняются после обновления страницы (в случае sessionStorage) и даже после перезапуска браузера (при использовании localStorage).

Но ведь у нас уже есть куки, зачем тогда эти объекты, подумали вы? \
`-` В отличие от куки, объекты веб-хранилища не отправляются на сервер при каждом запросе. Поэтому мы можем хранить гораздо больше данных. Большинство браузеров могут сохранить как минимум 2 мегабайта данных (или больше), и этот размер можно поменять в настройках. \
`-` Ещё одно отличие от куки – сервер не может манипулировать объектами хранилища через HTTP-заголовки. Всё делается при помощи JavaScript. \
`-` Хранилище привязано к источнику (домен/протокол/порт). Это значит, что разные протоколы или поддомены определяют разные объекты хранилища, и они не могут получить доступ к данным друг друга.


### Redux

Библиотека Redux — это способ управления состоянием приложения. Она основана на нескольких концепциях, изучив которые, можно с лёгкостью решать проблемы с состоянием.

3 принципа: \
`-` Single source of truth — store всегда один и он является источником истины всего приложения. \
`-` State is read-only — нельзя изменять state напрямую, для этого нужно вызвать action. \
`-` Reducer is a pure function — повторные вызовы редьюсера с одними и теми же аргументами возвращают одно и то же. Текущий state не мутируется, а клонируется (deep copy).

[Ключевые моменты](./materials/Redux.md)


**Упражнение 1.** \
У вас уже готово приложение для поиска покемонов — предлагаем его улучшить! Вам нужно сделать темную и светлую тему интерфейса для вашего приложения. Изменение темы должно происходить с помощью react context. В вашем context должно храниться поле 'isLight : boolean' (по дефолту true). В зависимости от значений в этом поле у ваших компонентов должны меняться/добавляться css классы. [Макет](./misc/images/Exercise_1_theme.jpg)   

**Упражнение 2.** \
Теперь давайте сделаем так, чтобы при каждом обновлении страницы приложение не отправляло запрос на получение дефолтного списка из 20 покемонов. Вам нужно выполнить этот запрос один раз и положить данные в localStorage. До тех пор, пока они там есть, заново запрос посылать не надо.

**Упражнение 3.** \
Теперь у вас появилась возможность избавиться от props drilling. Вам нужно создать общий стор, используя библиотеку redux для всего приложения. При первом рендере вашей странице данные из localStorage (если они там есть) кладутся в ваш стор, если данных нет, то надо отправить запрос, а результат положить и в localStorage, и в ваш стор. Теперь все операции добавления/удаления покемонов должны выполняться с помощью специальных actions и манипуляций со стором.

>Пожалуйста, оставьте обратную связь по проекту в [форме обратной связи.](https://forms.gle/jTXXqYLKXzbbst2y8)