[React Foundations](https://nextjs.org/learn/react-foundations) のチュートリアルコードです。
以下のことを知ることができました。
- JSX とは Javascript XML の略称であり、HTML ライクなコードスニペットを記述できる Javascript の拡張記法である。（参考：[Wrinting Markup with JSX](https://react.dev/learn/writing-markup-with-jsx)）
  - 例えば `return <div>{some value}</div>` のようなことができる。 
- React においてコンポーネントとは `関数` であり、HTML ライクなコードスニペットを返す。
- コンポーネントの引数（props と呼ぶ）は object 型であるが、[分割代入](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) を用いることにより使用するプロパティ名を明示することが可能。
  - 例えば `function Header({ title }) {...}` のようにコンポーネントを定義しておくと、呼び出し元で `<Header title='今日の料理' />` とやれば Header コンポーネントに `title='今日の料理'` が正しく伝わるが、`<Header Title='今日の料理' />` としても 'きょうの料理' という値は正しく引き渡されない。

