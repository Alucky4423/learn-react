# 03-rendering-elements

**要素はReactアプリケーションの最小ビルディングブロックです。**

要素は画面上で見たいものを記述します。

```jsx
const element = <h1>Hello, world<h1>;
```

ブラウザのDOM要素とは異なり、React要素は単純なオブジェクトであり、手軽に作成できる。
React DOMはReact要素と一致するようにDOMを更新します。

> **NOTE:**<br />
> 要素をより広く知られている｢コンポーネント｣の概念と混同する可能性があります。
> 要素とは、どの要素が「作られた」要素なのかということです。先に進む前にこのセクションを読むことをお勧めします。


## 要素をDOMにレンダリングする。

HTML fileのどこかに`<div>`があるとしましょう。

```jsx
<div id="root"></div>
```

これを｢ルート｣DOMノードと呼びます。その内部のすべてがDOMによって管理されているからです。

Reactだけで構築されたアプリケーションは、通常、単一のルートDOMノードを持っています。
しかし、Reactを既存のアプリに統合する場合、あなたは自由に多くの独立したルートDOMノードを持つことができます。

React要素をルートDOMノードにレンダリングするには、ReactDOM.render();に両方を渡します。

```jsx
const element = <h1>Hello, world</h1>;
ReactDOM.render(
  element,
  document.getElementById('root');
);
```

このページには、｢Hello, world｣と表示されます。


## レンダリングされた要素の更新

React要素は**不変**です。
要素を作成したら、その子要素や属性を変更することはできません。
要素はムービー内の一つのフレームのようなもので、特定の時点のUIを表します。

これまでの知識では、UIを更新する唯一の方法は、新しい要素を作成し、
それを`ReactDOM.render（）`に渡すことです。

この時刻の例を考えてみましょう。

```jsx
function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  ReactDOM.render(
    element,
    document.getElementById('root')
  );
}

setInterval(tick, 1000);
```

`setInterval()` コールバックから毎秒 `ReactDOM.render()`を呼び出します。

> **NOTE:** <br />
> 実際には、ほとんどのReactアプリケーションは`ReactDOM.render()`を一度しか呼び出しません。
> 次のセクションでは、そのようなコードがステートフルなコンポーネントにどのようにカプセル化されるのかを学習します。

