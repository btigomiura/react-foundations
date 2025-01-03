# プロジェクト概要
[React Foundations](https://nextjs.org/learn/react-foundations) のチュートリアルコードです。

# 学んだこと
以下の学びがありました。

1. JSX に関して
1. コンポーネントに関して
1. Clienet and Server Components

## 1. JSX に関して
JSX とは Javascript XML の略称であり、HTML ライクなコードスニペットを記述できる Javascript の拡張記法である。（参考：[Wrinting Markup with JSX](https://react.dev/learn/writing-markup-with-jsx)）
例えば以下のようなコードが該当する。
```jsx
function Header() {
  return <h1>Default title</h1>;
}
```
ほぼ HTML そのままで記述できるが、以下の点だけ注意が必要（参考：[The Rules of JSX](https://react.dev/learn/writing-markup-with-jsx#the-rules-of-jsx)）
1. コンポーネントの返り値（後述）に関しては何らかのタグで囲まれた状態にする必要がある（複数の div タグ等がフラットに並んだ状態で返すのはNG）。
どうしても div タグで囲みたくない場合は [Fragment](https://react.dev/reference/react/Fragment) (`<>` `</>`) で囲むのもあり。
1. タグは全て閉じた状態にする必要がある。念頭にあるのは `<img>` のような自己完結できるタグ。これらは `<img />` のようにして確実に閉じるようにする。
1. 基本 camelCase で全ての名前を記述する。Javascript 使ってるんだから当たり前か。
1. HTMLタグの中に javascript のコードを埋め込む場合、`{}` で囲むようにする。例えば `<h1>{title}</h1>` のような感じ。

## 2. コンポーネントに関して
React においてコンポーネントとは `関数` であり、前述の JSX コードスニペットを返すものである。下記がコンポーネントの例。
```jsx
function Header({ title }) {
  return <h1>{title ? title : 'Default title'}</h1>;
}
```
コンポーネント名は camelCase ではなく PascalCase で記述する点に注意。
また引数（props と呼ぶ）に関して、こちらは object 型なので、上の例であれば素直に
```jsx
function Header(props) {
  return <h1>{props.title ? props.title : 'Default title'}</h1>;
}
```
としても良いのだが、[分割代入](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) を用いることにより使用するプロパティ名を明示することが可能なのでこちらに寄せた方が保守性が上がる。

コンポーネントは他のコンポーネントから下記のような形で呼び出しが可能。
```jsx
function Body() {
  return (
    <div>
      <Header title="きょうの料理" />
      <p>Body</p>
    </div>
  );
}
```
ちなみに上記の `<Header />` タグで title 以外のパラメータを引き渡しても何も起こらない。

## 3. Client and Server Components
SPA とは異なり、あらかじめページのレンダリングができる部分はサーバー側でレンダリングし、ユーザー操作に応じて画面が変わる部分についてはクライアント（ブラウザ）側でレンダリングするような仕掛けになっている。

基本的にはサーバー側でレンダリングするものとして解釈されるが、ファイルの先頭に `"use client";` という文言を宣言しておくことで、`このファイルは Client 側でレンダリングするものですよ` と next.js 側に伝えることができる。
