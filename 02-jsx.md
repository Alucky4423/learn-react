# JSX

```javascript
const element = <h1>Hello world!!</h1>;
```

このコードは、HTMLでも文字列でもありません。

**JSX**というjavascriptの拡張構文です。


## JSXへの式の埋め込み

javascript式を**中括弧**で囲むことでJSXに埋め込むことができます。

> example : **[01-embedd.html](./01-embedd.html)**

```javascript
function sum(a, b) {
  return a + b;
}

const name = "React.js";

const elements = (
  <div>
    <h1>Hello {name}!!</h1>
    <p>1 + 1 = {sum(1, 1)}</p>
  </div>
);

ReactDOM.render(
  elements,
  document.getElementById('root')
);
```

> NOTE :
JSXを複数行に分割して書く場合は、自動セミコロン挿入を避けるためにカッコで囲うことをすすめます。


## JSXでの属性の指定

引用符を使用して文字列リテラルを属性として指定できます。

```javascript
const element = <div tabIndex="0"></div>
```

中括弧を使用して文字列リテラルを属性として埋め込むこともできます

```javascript
const element = <img src={picture.url} />
```

> **<span style="color:red;">WARNING</span>** : JSXはHTMLよりもJavaScriptに近いので、React DOMはcamelCaseHTML属性名の代わりにプロパティ命名規則を使用します。<br>
例えば、 `class` はJSXだと `className` に。 `tabindex` は `tabIndex` となります


## JSXによるインジェクションの防止

ユーザ入力をJSXに埋め込んでも大丈夫です

> example : **[02-injection.html](./02-injection.html)**

```jsx
const injection = "<br>";
const element = <h1>aaaa{injection}bbbb</h1>;

ReactDOM.render(
  element,
  document.getElementById('root')
);
```

ReactDOMはレンダリングする前にJSXに埋め込まれた値をエスケープします。
これにより**XSS**を防ぐことができます。


## 参考文献

> [introducing-jsx](https://facebook.github.io/react/docs/introducing-jsx.html)
