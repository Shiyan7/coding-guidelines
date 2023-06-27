
First, run the development server:

```bash
npm run dev
# or
yarn dev
```

### Структура
```
└────
    ├── pages
    │   ├── _app.tsx
    │   ├── index.tsx
    │   ├── **/*.tsx
    │   └── *.tsx
    ├── public
    │   ├── fonts
    │   │   └── *.woff2
    │   ├── sprites
    │   │   └── *.svg
    │   ├── favicon.svg
    ├── src
    │   ├── app
    │   │   └── styles
    │   │   └── providers
    │   │   └── HOCs
    │   │   ├── index.tsx
    │   ├── processes
    │   │   └── **/*.ts
    │   ├── pages
    │   │   └── **/*.tsx
    │   ├── widgets
    │   │   └── **/*.tsx
    │   ├── features
    │   │   └── **/*.tsx
    │   ├── entities
    │   │   └── **/*.tsx
    │   ├── shared
    │   │   └── api
    |   |   └── lib
    |   |   └── ui
    |   |   └── config
```

### Используйте нейминг файлов или папок только в стиле kebab-case, Все буквы маленькие, слова разделены дефисом.
```
src
└── pages
    ├── home
    │   ├── ui.tsx
    │   ├── styles.module.scss
    │   └── index.ts
    └── about-us
        ├── ui.tsx
        ├── styles.module.scss
        └── index.ts
```

## Гид по стилям

### 2 Пробела для отступа

Используйте 2 пробела, чтобы сделать отступ в коде, и поклянитесь никогда не смешивать табуляции и пробелы, иначе вас ждет ад 👹.

### 120 символов в строке

Ограничьте свои строки до 120 символов. Да, за последние несколько лет экраны стали намного больше, но не ваш мозг. Используйте дополнительную комнату для разделения экрана, ваш редактор поддерживает это, верно?

### Пробелы в комментариях
*Плохо:* ❌
```js
//This is a comment with no whitespace at the beginning

/*This is a comment with no whitespace at the beginning */
```
*Хорошо:* ✔️
```js
// This is a comment with no whitespace at the beginning

/* This is a comment with no whitespace at the beginning */
```
### Шаблоны в двойных кавычках
*Плохо:* ❌
```js
"Hello ${name}!";
'Hello ${name}!';
"Time: ${12 * 60 * 60 * 1000}";
```
*Хорошо:* ✔️
```js
`Hello ${name}!`;
`Time: ${12 * 60 * 60 * 1000}`;

someFunction(`Hello ${name}`);
```

### Двойные кавычки

*Плохо:* ❌
```js
import Name from 'file/path';

const foo = 'bar';
```
*Хорошо:* ✔️
```js
import Name from "file/path";

const foo = "bar";
```

### Двойные кавычки в тегах (jsx, tsx)

*Плохо:* ❌
```jsx
<input type='text' />
```
*Хорошо:* ✔️
```jsx
<input type="text" />
```

### Обязательный атрибут alt в тегах для картинок (jsx, tsx)

*Плохо:* ❌
```jsx
<area {...props} />

<img {...props} />

<input type="img" {...props}  />
```
*Хорошо:* ✔️
```jsx
<area alt="This is descriptive!" />

<img alt="This is descriptive!" {...props} />

<input type="img" alt="This is descriptive!" {...props} />
```

### Используйте camelCase
*Плохо:* ❌
```js
const user_name = "John";
```
*Хорошо:* ✔️
```js
const userName = "John";

/* ignore destructuring */
const { some_property, ...rest } = obj;
```

### Формат пробелов в объектах
*Плохо:* ❌
```js
import {isUndefined} from 'lodash';

const user = { name: 'John', age: 25 };

const { ...otherProperties } = obj;
```
*Хорошо:* ✔️
```js
import { isUndefined } from "lodash";

const user = { name: "John", age: 25 };

const { ...otherProperties } = obj;
```

### Не используйте var
*Плохо:* ❌
```js
var user_name = 'John';
```
*Хорошо:* ✔️
```js
const foo = "foo";
let bar = "bar";
```

### Неиспользуемые переменные
To avoid errors, remove unused variables.  

Во избежание ошибок удалите неиспользуемые переменные.

*Плохо:* ❌
```js
const arr = [1, 2, 3];
const someVar = "bla.com"
const items = arr.map((item, index) => `Counter: ${index}`);
```
*Хорошо:* ✔️
```js
const arr = [1, 2, 3];
const items = arr.map((_, index) => `Counter: ${index}`);
```

### Не используйте eval()
*Плохо:* ❌
```js
window.eval("var a = 0");
global.eval("var a = 0");
```
*Хорошо:* ✔️
```js
class A {
    foo() {
        // This is a user-defined method.
        this.eval("var a = 0");
    }

    eval() {}

    static {
        // This is a user-defined static method.
        this.eval("var a = 0");
    }

    static eval() {}
}
```

### Условный оператор используйте строгое сравнение ===
Программирование — это не запоминание [дурацких правил][операторов сравнения]. Используйте оператор тройного равенства, так как он будет работать так, как ожидалось.

*Плохо:* ❌
```js
const a = 0;
if (a == '') {
  console.log('losing');
}
```
*Хорошо:* ✔️
```js
const a = 0;
if (a !== '') {
  console.log('winning');
}
```

### Отдавайте предпочтение конструкции Switch вместо нескольких else-if (3)

*Плохо:* ❌
```js
if (foo === 1) {
    // 1
} else if (foo === 2) {
    // 2
} else if (foo === 3) {
    // 3
} else {
    // default
}
```
*Хорошо:* ✔️
```js
if (foo === 1) {
    // 1
} else if (foo === 2) {
    // 2
}
```
```js
switch (foo) {
    case 1: {
        // 1
        break;
    }
    case 2: {
        // 2
        break;
    }
    case 3: {
        // 3
        break;
    }
    default: {
        // default
    }
}
```

### Не используйте any || any[ ] типы

Если вы не знаете тип переменной, используйте Generic или unknown.

*Плохо:* ❌
```ts
interface User {
    name: any
}

interface Users {
    data: any[]
}
```
*Хорошо:* ✔️
```ts
interface User {
    name: string
}

interface Users {
    data: Array<User> | User[]
}
```
