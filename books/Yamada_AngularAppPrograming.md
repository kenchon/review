   　　　　　　　　　　　　　　　　　　　　　　　　 　　　　　　　 # 1.1 JavaScriptの歴史

JavaScriptフレームワークが登場するにいたる歴史的経緯を振り返る。

### JavaScriptの盛り上がり～不遇の時代
- 1990年代，JavaScriptベースのダイナミックHTMLという技術が流行った
	- 画面にアニメーション画像が走る
	- ページ切り替えにエフェクトがかかる
- しかし，これらが過剰に使われ，ページが重かった
- セキュリティホールが見つかったため，かなり限定的な環境じゃないと動かないようになった
- しばらくJavaScriptは不遇の時代を経る

### JavaScriptの復権
- 2005年，**Ajax**が登場した。
	- デスクトップ上で，デスクトップライクなページをつくれる
	- HTML，JavaScriptという標準的な技術でリッチなコンテンツが作れる
- ECMAによる標準化もあって，JavaScriptの見直しが図られた
- 2000年代後半にHTML5が登場，JavaScript APIが強化されていく
### JavaScriptライブラリから，JavaScriptフレームワークへ
- JavaScriptは生産性が高い言語とは言えない
	- ブラウザによって挙動が異なる問題
	- 特有の癖：プロトタイプベースと呼ばれる特殊なオブジェクト指向構文
	- 型の制約が緩い
- jQueryが一世を風靡，UI開発が容易になる。ただし，大規模開発は苦手
	- あくまでページ操作をサポートするライブラリである。例えば，見た目とビジネスロジックを明確に分離するようなアプリの構造化はできない。
➡ **以上の経緯から，大規模開発に向いた本格的なフレームワークが求められてきた**

# 1.2 フレームワークとは？
- フレームワークとは
>問題に対する定石（イディオム），または設計面での方法論を「再利用可能なクラス」という形でまとめたもの。
>言い換えると，アプリのコードを相互につなげるベース

- アプリ開発者は，フレームワークの基盤に沿って独自のコードを加えることで，一定の品質をもったアプリを作ることができる
- ライブラリとフレームワークはどう違うの？
	- **ライブラリ**：ユーザコードによって呼び出される。
	- **フレームワーク**：ユーザコードを呼び出す。
	- 後者は，アプリのライフサイクル（初期化から実処理，終了までの流れ）を管理しており，その要所要所で「なにをすべきか」をユーザコードに問い合わせる

## フレームワーク導入の利点
 - 開発生産性の向上
	- 同じルールを強制する。一貫性が保たれる
	- ユーザコードは機能ごとに相互に独立しているので，機能単位での役割分担をしやすく，大規模開発に向いている
- メンテナンス性に優れる
	- アプリの可読性が高い。問題個所の特定がしやすい
	- 同一のアーキテクチャを採用していれば，統合なども楽になる
	- 開発ノウハウを容易に引き継げる
- 先端の技術トレンドにも対応しやすい
	- フレームワークは日々更新される
	- セキュリティにも対応してくれる
- 一定以上の品質が期待できる
	- 自作アプリより「信頼性が高い」
	- 利用実績が長い
	- フレームワークを用いるということは，現在のベストプラクティスを導入するということ

## なぜAngularか
- 現時点でもっとも注目されるフレームワークのひとつである
- Googleが開発に携わっており，継続的なバージョンアップが期待できる
> ”人気やシェアは，フレームワークとしての良しあしを左右する決定的な基準ではありませんが，重要な要素ではあります。というのも，シェアの大きさは，様々なユーザの目にさらされ，実績を積み，支援されていることの証であり，そのまま「品質の高さ」「資料の豊富さ」「実績の蓄積」を物語っているからです”

## Angularの特徴
- フルスタックのフレームワーク
	- HTMLベースのテンプレートエンジン
	- ビジネスロジックを実装するためのサービス
	- URLに応じてページを振り分けるルーティング機能
	- 単体テスト・シナリオテストを支援するテストフレームワーク
	- など
- コンポーネント指向
	- コンポーネントは画面に複数配置できるし，階層構造にも出来る
	- Angularアプリとは，１つ以上のコンポーネントの集合である
	- コンポーネントは，ビュー，クラス，メタ情報の複合体
- JSの派生言語をサポートしているものの，TypeScriptで開発するのが無難
- Angularバージョンポリシー
	- バージョン番号は，「`メジャーバージョン`.`マイナーバージョン`.`パッチ`」で表現
	- パッチ：バグフィックスなどの微小な変更
	- マイナーバージョン：機能追加を伴うが，互換性は保たれる
	- メジャーバージョン：互換性が保たれないことがある破壊的な変更
- Angularは半年に一度バージョンアップする

## Angularアプリの構成部品：モジュール
### モジュールとは
- 関連するクラスをまとめて，モジュールとして扱う
	- **Angularアプリ**
		- `ルートモジュール`
			- コンポーネント，UI部品
			- サービス，ビジネスロジック
			- パイプ
			- ディレクティブ
		- `サブモジュール`
			- コンポーネント
			- サービス
		- `Angularモジュール`
			- Common Module
			- Http Module ...
			
	- アノテーション`@`：クラスを定義しただけでは，モジュールとはみなされない。`@NgModule`デコレータ―でモジュールとしての情報を宣言する必要がある。**デコレータ**とは，クラスやプロパティ，メソッド，引数などに対して，構成情報を付与するためのしくみ。

### サンプルアプリに含まれる構成物
- `app.component.ts`: ページを構成するUI部品を記述するコード
- `main.ts`: Angularアプリを起動するためのスタートアップコード
- `index.html`: メインページを準備する
- 設定ファイル:
	- `package.json`: Angular，またはアプリ本体で利用するライブラリ情報などを定義
	- `tsconfig.json`: TypeScriptコンパイラの動作を定義
	- `systemjs.config.js`: モジュールローダー(SystemJS)の設定情報
		- 呼び出したファイルの拡張子を省略したときの挙動の記述
		- `baseURL`などの設定

### サンプルアプリの利用方法


# 3. データバインディング
データバインディングとは？
>Angularアプリで画面（コンポーネント）を制御するうえで欠かせない仕組み。データバインディングを使用することで，コンポーネントの値をテンプレートに反映したり，テンプレートの変化をコンポーネントに伝達したり，といった仕掛けを限りなくコーディングレスで実装できます。

言い換えると，コンポーネント（C）とテンプレート（ビュー＝V）とを紐づけるための仕組み。

データバインディング構文

| データの方向 | 種類        | 記法 |
|--   |--                  |--          |
| C→V | Interpolation(補間) | `{{...}}` |
| C→V |プロパティ・属性バインディング|`[property]="value"`|
| C←V |イベントバインディング|`(event)="handler"`|
| C⇔V |双方向バインディング|`[(target)]="value"`|

ポイント：**バインド方式によって記法が異なる**

## 3.2 Interpolation構文

### ・`{{...}}`式
- テンプレートに埋め込む値を，コンポーネントのプロパティとして定義する
例：①で定義した`name`プロパティを②で`{{name}}`として参照する
```javascript
import { Component } from  '@angular/core';
@Component({
	selector:  'my-app',
	template:  `<h1>Hello {{name}}</h1>`, //②
})
export  class  AppComponent { name  =  'Angular'; } //①
```

補間の中身では，JavaScriptの構文が使える。ただし，以下の点に注意：
- 式が副作用を伴わない；ほかの値に影響が出ない
- 短時間で実行できる
- シンプルである
- 冪等である；同じ操作を繰り返して実行しても同じ結果を返す

`{{...}}`は何度も繰り返されるので，アプリが重くなる原因になることを避ける。

### ・`?.`演算子(Safe Navigation Operator)
```javascript
import { Component } from  '@angular/core';
@Component({
	selector:  'my-app',
	template:  `<h1>Hello {{member.name}}</h1>`, //①
})
export  class  AppComponent { 
	member = {
		name = '山田太郎',
		age = 30
	};
}
```
`member`プロパティをコメントアウトした状態で，これを実行すると，①で例外が発生する。
例外に対処するためには，nglfディレクティブを使って，あらかじめundefined/nullチェックを行えばよいが，コードが冗長になってしまう。ここで，①を次のように書き換えると，例外が発生しなくなる。
```javascript
	template:  `<h1>Hello {{member?.name}}</h1>`, //①'
```
これによって，オブジェクト`member`が空であるかどうかを確認し，から出ない場合のみに`name`プロパティにアクセスするので「安全」である。

## 3.3 プロパティバインディング
プロパティバインディングによって，要素のプロパティに対して値をバインドできる。
要素とは，例えばHTML要素などがある。

```javascript
import { Component } from  '@angular/core';
@Component({
	selector:  'my-app',
	//ブラケット構文
	template:  `<img [src]="image" />` //①
	//bind-xxxxx属性
	//template: `<img bind-src="image" />`　//②
	//Interpolation
	//template: `<img src="{{image}}" />` //③
})
export  class  AppComponent {
	image  =  'http://www.wings.msn.to/image/wings.jpg';
}
```
①では，`"image"`は文字列ではなく，プロパティを表す変数となる。
他にも，②，③などの書き方があるが，プロジェクトで統一するのが良い。

### HTML文字列をバインディングする
```javascript
import { Component } from '@angular/core';

@Component({
  selector: 'my-app',
  template: `<div>{{msg}}</div>`
})
export class AppComponent {
  msg: string = `Hello World!`　// ①
}
```
ここで仮に，①をHTMLのコードにした場合，HTML文字列はエスケープされて生の文字列が表示される。これは，意図しないタグを埋め込まれたりする脆弱性を残してしまうためである。このような攻撃をクロスサイトスクリプティングという。

ただし，HTMLを埋め込みたいときもある。その時は，
```javascript
@Component({
  selector: 'my-app',
  template: `<div [innerHTML]="msg"></div>`
})
```
とする。

ただし，HTMLのタグなどはそのままうめこまれるわけではなく，できるだけ脆弱性が残らないようにサニタイズされる。自分が意図したHTMLタグをすべて埋め込みたいなら，信頼済みマークを付ける必要がある。(参照：`bypassSecurityTrustHtml`メソッド)

### イベントバインディング
- マウスクリックなどに対応したバインディング。
- キーボード操作に関するイベント取得もできる。

#### イベントのデフォルト動作のキャンセリング：
- ふつうは，キーが入力されたら文字が画面に出てくる
- でも，入力フォームが郵便番号入力フォームだったら，数字以外入力ができないようにできる
- 参照：`e.preventDefault();`

#### バブリング
- 下位要素の操作が，上位要素に伝播すること
- 時に望ましくないので，`e.stopPropagation()`でブロックできる

>**コラム**
>`log.console("log output")`で，開発者ツールのコンソール出力を得られる。

#### Enterキーのイベント：`keyup.enter`
エンターキーは使用頻度が高いので，それ専用のイベントが存在。

### 双方向バインディング
- ビューへの変更がコンポーネントに伝わり，かつ，コンポーネントの変更もビューに伝わる。
- 実装方法はいろいろあるが，その一つが`ngModel`を用いる方法。
	- `[(ngModel)]="myName"`・・・`myName`オブジェクトに値が入ると，コンポーネントへの代入が行われる。逆も起こる。

# 4. 標準パイプ/ディレクティブ
とは？
>パイプ/ディレクティブとは，テンプレートで利用できるAngularの構文である。パイプは，与えられた式の値を加工・成形する機能，ディレクティブは条件分岐・繰り返し，スタイル定義など，文書ツリーを操作する機能を，それぞれ提供する。

## パイプ
- `{{price | currency: 'JPY'}}`: `price=1444`のとき，`JPY1,444`に加工される。
- さらにパイプをつけて，それに対して追加の処理を行うことができる。

Angular標準パイプ：
- lowercase, percent, number, slice ...
- `i18nPlural`: 数値によって場合分け
- `i18nSelect`: 文字列によって場合分け　

>もっとマシなパイプ名はなかったのか？

## ディレクティブ
ページに付加するカスタムの機能・要素。
- コンポーネント：テンプレートを伴ったディレクティブ
- 構造ディレクティブ：要素を追加・削除することで，文書ツリーを変更
- 属性ディレクティブ：属性の形式で，要素・コンポーネントの見た目や動作を変更

### スタイルの変更
ボタンを押すと，コンポーネントの背景色と文字色が変更される：
```javascript
import { Component } from '@angular/core';

@Component({
  selector: 'my-app',
  template: `
    <input type="button" (click)="back=!back;fore=!fore" value="Background"/>
    <div [ngStyle]="styles">
    {{msg}}
    </div>`
})

export class AppComponent {
  msg: string = `Hello World!`;
  back = false;
  fore = false;
  get styles(){
    return {
      'background-color': this.back ? '#12346b': '',
      'color': this.fore ? '#fff': '',
      fontWeight: 'bold',
      margin: '15px',
      padding: '15px'
    };
  };
}
```
ボタン押す前：
# TODO: add pictures

# 5. フォーム開発
> フロントエンド開発において，フォームはエンドユーザからの入力を受け取る代表的な手段です。Angularはユーザからの入力を受けて，処理を開始し，その結果をテンプレートに反映する。

## 5.1 フォーム開発の基本
- Angularでは，`<form>/<input>`要素が拡張されており，リッチなフォームを簡単なコードで実装できる。
- 入力内容の検証などもできる
- 

# 6. コンポーネント開発
Angularは，コンポーネント指向のフレームワークである。コンポーネントは以下の役割を受け持つ：
- ビューを整形する
- バックエンドにビューの情報を引き渡す
- バックエンドの情報をビューに引き渡す
- 本章では，複数のコンポーネントを連携させる方法を学ぶ

[参考：BFF（Backends For Frontends）超入門](https://www.atmarkit.co.jp/ait/articles/1803/12/news012.html)
>マイクロサービス/API時代のフロントエンド開発に求められる技術の1つBackends For Frontends（BFF）について解説する連載。初回は「超入門」としてBFFの概要や事例を中心に紹介する。

コンポーネントの定石：
```js
import { Component } from '@angular/core';
...
@Component({
	selector: 'my-app',
	template: `
		<h1>Hello, World!</h1>
	`
	//templateUrl: './detail.component.html'  // templateUrl でパスを記述してもよい。
})
export class DetailComponent {
	onclick(){
		...
	}
}
```

## 階層的なコンポーネント
- 基盤となる`AppComponent`の中で，子`ChildComponent`を呼び出すような入れ子構造を作れる。
- 複数コンポーネントが相互にコミュニケーションする場合がある。そうしたとき，子コンポーネントは，親コンポーネントへの入出力時に，`@Input`，`@Output`アノテーションを用いることができる。
- **テンプレート参照変数**を用いる方法でも子コンポーネントを参照できる。

## コンポーネントのライフサイクル
大まかな流れ：
>コンポーネントは，まず最初に生成された後，プロパティ・子コンポーネントの経k名を受けて状態（表示）を変化させていき，非表示になるタイミングで破棄される。

- Angularには，ライフサイクルの変化を受けて呼び出される様々なメソッドがあり，**ライフサイクルメソッド**と呼ばれる。
- `ngOnInit()`，`ngOnDestroyed()` －ページの初期化，終了処理－などが内部的に行われて，画面の生成などが管理される。でも，これらを明示的に呼び出すこともできる。
- 明示的に呼び出すことのメリットは，ライフサイクルの切り替わり時に，特定の処理を呼び出せるようになること。

### `ngOnChanges()`
プロパティが変化したときに呼び出される。

```typescript:明示的に実装した例
ngOnChanges(changes: SimpleChanges) {
  console.log('［child］ngOnChanges');
  for (let prop in changes) {
    let change = changes[prop];
    console.log(`${prop}：${change.previousValue} => ${change.currentValue}`);   
  }
}
```
- `SimpleChanges`
	- 「`プロパティ名：変更情報`」のハッシュ。
	- `.previousValue`, `.currentValue`などのメンバーを持っている。

### `ngAfterViewInit(), ngAfterViewChecked()`
ビューの初期化・変更時の処理を実装する。
- `ngAfterViewInit()`：ビューが初期化されるときにのみ呼び出される
- `ngAfterViewChecked()`：ビューが変更されるときに呼び出される
- `<ng-content></ng-content>`：呼び出し元のコンポーネントから，子コンポーネントへの埋め込みを行うときに使う。細かい使い方は`p.200`参照。
- `@ViewChild()`：現在のビューに配置された子コンポーネントを参照するためのデコレータ。子コンポーネントが複数ある場合は`@ViewChildren()`を使う。

### `ngAfterContentInit(), ngAfterContentChecked()`
外部コンテンツの初期化・変更時の処理を実装する。
- `ngAfterContentInit()`：ビューが初期化されるときにのみ呼び出される
- `ngAfterContentChecked()`：ビューが変更されるときに呼び出される
- `@ViewContent()`：外部コンテンツで定義された子コンポーネントを参照するためのデコレータ。

## 6.3 コンポーネントのスタイル定義
- `@Component`デコレータのstyle・styleUrlsパラメータを指定することで，コンポーネントのスタイルを変えられる。
- コンポーネントの中で定義されたスタイルは，閉じており，他のところで定義されたものと衝突しない。
- つまり，`app.component.ts`のテンプレート内で定義された`<p>`には反映されても，`index.html`で定義された`<p>`にはスタイルは反映されない。
- スタイル定義は`app.component.css`として外部化することができ，`styleUrls`パラメータで指定することもできる。

**スタイル指定のベストプラクティス**:
望ましい順に，
- `template`の`style`・`styleUrls`パラメータで指定する
- `@import`ディレクティブを用いる。
```javascript
@import 'app.component.ext.css';
```

# 

# 10 テスト
Angularでは，ユニットテスト・E2Eテスト（シナリオテスト）をサポートしている。

## 10.1 テストの基本
- ユニットテスト	：サービス，コンポーネント，ディレクティブ，パイプなどの個々の構成要素をテスト
- E2Eテスト			：インテグレーションテスト，シナリオテストと同義。複数コンポーネントやビューにまたがるテスト

>サービス：親子関係にないコンポーネント間でデータを共有するためのしくみ。

## 10.2 ユニットテスト
#### テスティングフレームワーク：
JavaScriptには，テスティングフレームワークが色々あるが，Angularでは標準でJasmineを使用。
>**Jasmineの利点**：
>BDD形式の構文を利用し，テストコードを英文に近い構文で，アプリの振る舞いを表現できる。

#### テストランナー：
Jasmineにも，標準のテストランナーがついており，それがKarma。

#### Karmaの設定ファイル
`karma.conf.js`：
```js
// Karma configuration file, see link for more information
// https://karma-runner.github.io/0.13/config/configuration-file.html

module.exports = function (config) {
  config.set({
    basePath: '',  // <---- files, excludeパラメータなどの基底パス
    frameworks: ['jasmine', '@angular-devkit/build-angular'],
    plugins: [     // <---- Karmaプラグイン
      require('karma-jasmine'),
      require('karma-chrome-launcher'),
      require('karma-jasmine-html-reporter'),
      require('karma-coverage-istanbul-reporter'),
      require('karma-junit-reporter'),
      require('@angular-devkit/build-angular/plugins/karma')
    ],
    client:{
      clearContext: false // leave Jasmine Spec Runner output visible in browser
    },             // <---- テストアダプタの追加パラメータ
    coverageIstanbulReporter: {
      dir: require('path').join(__dirname, 'coverage'), reports: [ 'html', 'lcovonly', 'cobertura' ],
      fixWebpackSourcePaths: true
    },
    
    // reporters: ['progress', 'kjhtml', 'junit'],
    reporters: ['progress', 'kjhtml', 'coverage-istanbul', 'junit'],
    junitReporter: {
      // 出力ディレクトリ
      outputDir: require('path').join(__dirname, './coverage'),
      // 出力ファイル名
      outputFile: 'test-report.xml',
      suite: '',
      useBrowserName: false
    },
    port: 9876,
    colors: true,      // ログのカラー出力
    logLevel: config.LOG_INFO,
    autoWatch: true,
    browsers: ['Chrome', 'ChromeHeadless'],
    singleRun: false,  //　テスト後にすぐ終了するかどうか
  });
  process.env.CHROME_BIN = require('puppeteer').executablePath();
};
```

#### ユニットテストコード
```ts
import { async, ComponentFixture, TestBed } from '@angular/core/testing';

import { DeleteConfirmModalComponent } from './delete-confirm-modal.component';
// テストコードではまず，全体をdescribeで囲う。
describe('DeleteConfirmModalComponent', () => {
  let component: DeleteConfirmModalComponent;
  let fixture: ComponentFixture<DeleteConfirmModalComponent>;

  beforeEach(async(() => {
    TestBed.configureTestingModule({
      declarations: [ DeleteConfirmModalComponent ]
    })
    .compileComponents();
  }));

  beforeEach(() => {
    fixture = TestBed.createComponent(DeleteConfirmModalComponent);
    component = fixture.componentInstance;
    fixture.detectChanges();
  });

  it('should be created', () => {
	fixture.detectChanges();  // Angularの変更検地を実行する。明示的に設定しないといけない。
    expect(component).toBeTruthy();
  });
});
```
- `describe()`で囲う
	- describe(name, specs)
		- `name`：テストスイートの名前
		- `specs`：テストケース
	- テストスイートとは，関連するテストのまとまりを表す入れ物のようなもの。
- `beforeEach()`で初期化処理を行う。初期化しないなら呼び出さなくてもいい。
- `afterEach()`で終了処理。
- `it()`メソッドが，個々のテストケース。
	- it(name, test)
		- `name`：テストケースの名前
		- `test`：テストの内容
- `expect()`でテスト検証

## 10.3 ユニットテスト

- `TestBed`のメソッド
	- `configuretestingModule(def)`：テスト対象のコンポーネントを本来のアプリモジュールから切り離す。
	- `createComponent(comp)`：コンポーネントをインスタンス化する

>**分離単体テスト**
>コンポーネントは，Angularに強く依存しているため，テスト専用のTest APIが用意されているが，パイプ・サービスのテストは標準的なJasmineのAPIで行うことができる。後者を，分離単体テストという。後者の場合，ソースコードがシンプルで見やすくなるため，こっちの方が推奨される。

- コンポーネントの中に外部テンプレートが含まれる場合，読み込んだときに`.compileComponents()`でコンパイルする必要がある。

>**テスト駆動開発**
>- 最初にテストを書き，とりあえずの実装を行い，より洗練させていくという開発スタイル。
>-  "Clean code that works" が目標。そのために，まずテストに通るコードを作成し，それをリファクタリングする方法をとる。

>**ビヘイビア駆動開発**
>- コードレベル，ユーザレベルで，期待される振る舞いをテストコードに記述する。
>- 自然言語に近い形で，振る舞いを記述できるフレームワークが多いらしい。

### コンポーネントのテスト
**コンポーネント**のテストコード例：
```js
import { AppComponent } from './app.component';
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { ComponentFixtureAutoDetect } from '@angular/core/testing';

import { By }           from '@angular/platform-browser';
import { DebugElement } from '@angular/core';

// テストスクリプト本体（は，describe()で囲まれる）
describe('AppComponent', function () {
  let de: DebugElement;
  let comp: AppComponent;
  let fixture: ComponentFixture<AppComponent>;

  beforeEach(() => {
    // テストモジュールを準備
    TestBed.configureTestingModule({
      declarations: [ AppComponent ],
      // ComponentFixtureAutoDetect を用いると，detectChanges()しなくても変更検知してくれるようになる。
      providers: [
        { provide: ComponentFixtureAutoDetect, useValue: true }
      ]
    });
    
    // コンポーネントをインスタンス化
    fixture = TestBed.createComponent(AppComponent);
    comp = fixture.componentInstance;
    //テスト対象の要素を取得
    de = fixture.debugElement.query(By.css('h1'));
  });
  
  // <h1>要素の配下に「angular」の文字列が含まれているかを検証
  it('<h1>要素のテキストを確認', () => {
    fixture.detectChanges();
    const h1 = de.nativeElement;
    expect(h1.innerText).toMatch(/angular/i);
  });
  
  // nameプロパティの更新がテンプレートに反映されているかを検証
  it('nameプロパティの変化を確認', () => {
    comp.name = 'JavaScript';
    fixture.detectChanges();
    const h1 = de.nativeElement;
    expect(h1.innerText).toMatch(/javascript/i);
  });
});
```

- `TestBed`：ユニットテストのための環境を初期化・設定するためのクラス
- `createComponent(comp)`：コンポーネントのインスタンス化を行う。返ってくるオブジェクトは，`ComponentFixture`オブジェクトである。

### 外部テンプレートを含むコンポーネントのテスト
- コンポーネントに外部テンプレートが含まれる場合，テストも若干複雑になる。
- `beforeEach(async({外部テンプレートのコンパイル}))` みたいな形で，非同期的に外部テンプレートのコンパイルを行う必要があるらしい。そうすると，ここでの処理が終わった後に後続の処理が呼ばれる（なぜそうする？）

例：
```js
import { DebugElement } from '@angular/core';
import { async, ComponentFixture, TestBed } from '@angular/core/testing';
import { By }           from '@angular/platform-browser';

import { AppComponent } from './app.component';

describe('AppComponent', function () {
  let des: DebugElement[];
  let comp: AppComponent;
  let fixture: ComponentFixture<AppComponent>;

  beforeEach(async(() => {
    TestBed.configureTestingModule({
      declarations: [ AppComponent ],
    })
    .compileComponents();
  }));

  beforeEach(async(() => {
    TestBed.configureTestingModule({
      declarations: [ AppComponent ],
    })
    .compileComponents()
    .then((result) => {
      fixture = TestBed.createComponent(AppComponent);
      comp = fixture.componentInstance;
      des = fixture.debugElement.queryAll(By.css('tr'));
    });
  }));

    beforeEach(() => {
      fixture = TestBed.createComponent(AppComponent);
      comp = fixture.componentInstance;
    });

  it('テーブルの行数を確認', () => {
    fixture.detectChanges();
    des = fixture.debugElement.queryAll(By.css('tr'));
    expect(des.length).toEqual(6);
  });
});
```

- 最初の`beforeEach()`でコンパイルを，後続の`beforeEach()`でインスタンス化を行う。
- ここに特記すべきことではないが，`beforeEach()`は，後続の複数のテストに共通する前処理を行うためのものである。

### 入出力を伴うコンポーネントのテスト
- `@Input`デコレータで修飾されたプロパティは，普通に代入操作をすることで入力操作を再現する。
- `@Output`の方はかなりややこしいので p.405 参照。

### サービスに依存したテスト
- コンポーネントが依存するサービスをそのままテストコードに注入するのはよくない。
	- ビューはビューの機能，サービスはサービスの機能に徹するべき。
	- 問題を特定しにくくなる
	- 開発状況によっては，依存するサービスがまだ完成していないこともある
	- 時間に依存するものなどがあると，結果の再現性や実行時間の問題がでてくる
	- 依存サービスが外部サービスにアクセスする場合，テストのためのサーバ環境を準備する必要がある

上記の問題解決のために，**テストダブル** を用いる
- $double$...代役
- テスト対象が依存しているサービスを，ダミーのオブジェクトに置き換える
	- あらかじめ用意された結果を返すオブジェクトを，スタブ(stub)という。

## 10.4 E2Eテスト
- Protractorというテストランナーを用いるのが一般的。
- Protractorでは，内部的にSelenium WebDriverが用いられている。
- Selenium では，ブラウザへの文字入力やボタンクリック，画面遷移などの仕組みを備えている。

### protractor 設定ファイル
- 設定ファイル `protractor.config.js` で，利用ブラウザや，テストフレームワーク，対象のコードなどを指定できる。
- 対象とするコードは，設定ファイル内の `specs: []` の中で，ワイルドカードで一括で指定できる。

### e2eテストコード `.e2e-spec.ts`
> 百聞は一見に如かず

`app.e2e-spec.ts`
```js
import { browser, element, by } from 'protractor';

describe('QuickStart E2E Tests', function () {

  let expectedMsg = 'Hello Angular';

  beforeEach(function () {
    browser.get('');
  });

  it('遷移のテスト', function() {
	// ページタイトルの確認
    expect(browser.getTitle()).toEqual('Angular QuickStart');
    expect(element(by.css('h2')).getText()).toEqual('メインページ');
    // リンクをクリックしてページを移動
    element(by.linkText('Exampleページ')).click();
    expect(element(by.css('h2')).getText()).toEqual('Example');
  });
});
```
- ブラウザを操作する`browser`オブジェクト
    - 中でも`get`メソッドはよく使われる。設定ファイルで指定した`baseURL`以降のURLを引数として，そのページを開く。
    - `browser`オブジェクトには，ページをn秒間休止する，ページを閉じる，ページのソースを取得する，などの便利メソッドがある。
- `element/element.all` メソッド
    - アプリにアクセスした結果を確認するためのメソッド。`element/element.all`で，単一/複数 の要素を取得する。詳細：[Protractor API]([https://www.protractortest.org/#/api?view=ElementArrayFinder](https://www.protractortest.org/#/api?view=ElementArrayFinder))
    - elementはlocatorオブジェクトを引数としてとり，locatorには，`css`，`id`などのセレクターがある。
 - 要素には，クリックをしたり，テキストを取得するための豊富なメソッドが存在。
 - element.allは配列オブジェクトをとってくるので，配列にアクセスするためのメソッドがある。
 - `it()`が１テストケースに対応する。`xit()`にすることでそのテストケースだけexcludeできる。これは，テストスイートを記述する`describe()`についても同様，`fdescribe()`，`xdescribe()`みたいにして，`ng e2e`実行時にテストスイートを実行するかどうかを選択できる。

### 表要素の取得 - 対象の要素のHTMLタグに`id='<name>'`をつける
- 下記の`element.all()`を使わずに，表要素のテストを行う方法。
- 対象とする表項目`<td>`を`<td id='item'>`に変更する。
```js
element.all(by.id('item')).then(function(array) {
  // 表項目の特定の列の要素の，上から0番目のテキストを取得し，比較
  expect(array[0].getText()).toEqual('item_name'); 
});
```
### 表要素の取得 - 正統な方法`element.all(by.repeater('<class name>'))`
- 表の要素数などを配列でとりたいときに使う。
- あらかじめ，表要素の`<tr>`の中に`ng-repeater="<class name>"` みたいな感じで埋め込む。
code
```js
    element.all(by.repeater('<class name>')).count().then(function(size) {
      arrayLengthAfter = size; // Promise オブジェクトの中身ができたときに実行される。
    });
```



# 11 Angular 関連ライブラリ・ツール
- Angularの標準機能だけでは冗長になりやすい，目的に特化した機能
	- アコーディオンパネル，検証機能，国際化対応
- アプリ開発で利用できるツール
	- コードの骨組みを構成するAngular CLI，ブラウザでのアプリデバッグを容易にするAugury
	- アプリを高速化するAoT（事前コンパイル）

#### ngx-bootstrap
- class属性を付与するだけでリッチなデザインを実装できる。
- 単一のソースで画面サイズに応じた最適な表示を実装できる。
- トグルボタン，タブパネルなど，いい感じのデザインがつかえる。

#### ng2-validation
- パスワード入力欄の入力値の検証機能。
- 検証ルールが準備されており，コーディングしなくてもそれらを利用でき冗長化を避けられる。

#### Angular CLI
- アプリのひな型を自動生成する
- `ng new <project-name>`…で雛型生成
- `ng serve`…アプリ実行


## テスト Angular公式ページの解説
[カバレッジレポート](https://angular.jp/guide/testing#%E3%82%AB%E3%83%90%E3%83%AC%E3%83%83%E3%82%B8%E3%83%AC%E3%83%9D%E3%83%BC%E3%83%88%E3%82%92%E6%9C%89%E5%8A%B9%E3%81%AB%E3%81%99%E3%82%8B)

# その他
## CORS - Cross-Origin Resource Sharing
- クライアント・フロントエンド・バックエンド のように，クライアントがアクセスするリソース先のドメインが２つあるような場合，バックエンドはCORSという仕組みを使って，フロントエンド以外からのアクセスを制限できる。
- CORSは，HTTPヘッダに特定の要素を追加することで実現できる。
参考：[https://dev.classmethod.jp/etc/about-cors/](https://dev.classmethod.jp/etc/about-cors/)

## DOM：Document Object Model
JavaScriptでHTMLの要素を操作するための仕組み。例えば，`<img src="sample.jpg">`の中身を変更して画像をさしかえるといった操作をjs側からできる。

### DOMの階層構造
```html
<html>  
	<head>  
		<title>DOMってなにー？ │ JavaScriptのサイト</title>  
	</head>  
	<body>  
		<h1>JavaScriptのサイト</h1>  
		<h2>DOMってなにー？</h2>  
		<p><strong>Document Object Model</strong>の略称です。</p>  
	</body>  
</html>
```
![](http://piyo-js.com/05/images/img_dom.gif)

引用：[JavaScript 入門講座 DOMとは，](http://piyo-js.com/05/dom.html)

### 使い方，実装

> 例えば、標準 DOM は以下のコードにおける `getElementsByTagName` メソッドが文書内のすべての `<P>` 要素のリストを返さなければならないと定義しています。
> [https://developer.mozilla.org/ja/docs/Web/API/Document_Object_Model/Introduction](https://developer.mozilla.org/ja/docs/Web/API/Document_Object_Model/Introduction)
```js
var paragraphs = document.getElementsByTagName("P");
// paragraphs[0] は最初の <p> 要素
// paragraphs[1] は 2 番目の <p> 要素...
alert(paragraphs[0].nodeName);
```

# Snipets

## Modal表示に関する諸々

**`index.html`**
```html
<div class="modal-header">
	<h4 class="modal-title">{{'E.APIKEY.WORK.CONFIRM_MODAL.TITLE' | translate}}</h4>
</div>
<div class="modal-body">
	<p>{{'E.APIKEY.WORK.CONFIRM_MODAL.MODAL_MSG' | translate}}</p>
</div>
<div class="modal-footer">
	<button type="button" class="btn btn-outline-secondary" (click)="activeModal.close(false)">
	{{'E.APIKEY.WORK.CONFIRM_MODAL.MODAL_NG_BTN' | translate}}</button>
	<button type="button" class="btn btn-danger" (click)="activeModal.close(true)">
	{{'E.APIKEY.WORK.CONFIRM_MODAL.MODAL_OK_BTN' | translate}}</button>
</div>
```
- `<p>`：１つの段落であることを示すタグ，いい感じの改行がなされる。
- `<div>`：`<DIV>`タグはそれ自身は特に意味を持っていないが、`<DIV>～</DIV>`で囲んだ範囲をひとかたまりとして、 align属性で位置を指定したり、スタイルシートを適用するのに用いる。
- `<span>`：単体では特に意味を持たないタグだが、`<span>～</span>`で囲った部分をインライン要素としてグループ化することができる。

**`app.component.ts`**
```typescript
import { Location } from '@angular/common';
import { NgbActiveModal } from '@ng-bootstrap/ng-bootstrap';
import { Component, OnInit, Input } from '@angular/core';

@Component({
  selector: 'mp-e-apikey-confirm-modal',
  templateUrl: './confirm-modal.component.html',
  styleUrls: ['./confirm-modal.component.scss']
})
export class ApiKeyConfirmModalComponent implements OnInit {
  constructor(
    public activeModal: NgbActiveModal,
    private location: Location
  ) {
    this.location.subscribe((event: PopStateEvent) => {
      if (event.type === 'popstate') {
        this.activeModal.close(false);
      }
    });
  }
  ngOnInit() { }
}
```