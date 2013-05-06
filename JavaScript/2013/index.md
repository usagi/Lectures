# JavaScript 講座 2013年度版 資料

## 本資料の目次

1. [本講座について](#1-)
1. [JavaScript 概説](#2-javascript-)
1. [ES5 基礎](#3-es5-)
1. [現状のJavaScript開発とES6](#4-javascriptes6)
1. [課題](#5-)
1. [連絡等](#6-)

----

## 1. 本講座について

### 1.1. 開講

学校行事、国民の祝日を除き以下の通り開講します。

- 2013年5月 - 2013年10月
    - 曜日: 火曜日, 木曜日
    - 時限: 4-5-6 コマ（連続）

- 概要
    - コマ量: 6 [コマ/週] = 24 [コマ/月]
    - 計: 120 [コマ/講座]
        - 5月 : 24 [コマ]
            - 講座ガイダンス
            - 環境準備
            - ES5 概論・言語基礎
        - 6月 : 24 [コマ]
            - ES5 概論・言語基礎(続)
            - モダンES開発 概論
            - プロジェクト演習
                - チーム編成
                - 企画プレゼンテーション
        - 7月 : 24 [コマ]
            - プロジェクト演習
        - 8月 : 24 [コマ]
            - プロジェクト演習
                - 中間プレゼンテーション
        - 9月 : 0 [コマ]
            - 夏休み
        - 10月 : 24 [コマ]
            - プロジェクト演習
                - 最終プレゼンテーション

### 1.2. 対象者

1. C++、Java、C#、等の静的型付けC系OOP言語の経験者
1. 計算機・情報技術についてIPA基本情報技術者相当の基礎知識を有している者
1. 対象者として不足な知識がある場合は各自で補う努力を怠らない者

### 1.3. 目的

1. JavaScriptとはどの様なものか概要を知る
1. 最新のJavaScript開発に対応可能な基礎知識を獲得する
1. 実践的なJavaScript開発経験を得る

### 1.4. 推奨環境

本講座では下記環境を標準として進めます。

1. ハードウェア
    1. CPU: x86\_64
    1. GPU: OpenGL ES 2.0 対応
    1. 教室でインターネットに接続可能な事
1. OS
    - Linux Mint 14
    - Ubuntu 13.04
1. ウェブブラウザー
    - Chromium 25
1. JavaScript処理系
    - nodejs 0.6
        - npm 1.1
1. 文字コード
    - UTF-8
1. テキストエディター
    - Vim
    - Emacs
    - Sublime

講座への参加はCPUがARMでもTegraでもOSがOSXでもWindowsでもウェブブラウザーがFirefoxでもシェルがcmd.exeでもbashでもCUI環境しか用意しなくとも、何れなんでも構いません。
但し、非標準の環境でのトラブルシュートは基本的には自己責任とします。

講座の第一回目の時間は環境構築に費やす時間として与えます。
OSから用意するも良し、仮想環境を構築するも良し。
但し、少なくともChromium（Chromeでも講座で使う分には困りません）、Node.jsとnpm、TypeScriptはシステムに導入して置くと良いでしょう。

- [Node.js](http://nodejs.org/)
- [TypeScript](http://www.typescriptlang.org/)
    - [Linux Mint 14 + Raring で TypeScript 処理系を用意する](http://blog.wonderrabbitproject.net/2013/05/linux-mint-14-raring-typescript.html)

また、テキストエディターは標準でUTF-8を扱える状態で用意し、必要と思われるシンタックスハイライティングやその他の機能群を有効にしておくと良いでしょう。

### 1.5. 教材

1. [Standard ECMA-262 ECMA Script&reg; Language Specification](http://www.ecma-international.org/publications/standards/Ecma-262.htm)
    - 現行標準のECMAScriptの言語仕様書
    - ES5.1までについては、全てこれに書いてある
    - ES5.1の仕様を確認する際はググるより先に読む事
1. [Mozilla Developer Network / JavaScript](https://developer.mozilla.org/ja/docs/JavaScript)
    - 本講座の第3章の一部教材として採用
    - 内容がMozillaに偏りがちな点には注意する事
    - [JavaScript リファレンス](https://developer.mozilla.org/ja/docs/JavaScript/Reference)
    - [JavaScript ガイド](https://developer.mozilla.org/ja/docs/JavaScript/Guide)
1. [Codecademy JavaScript](http://www.codecademy.com/)
    - 本講座の第3章の副教材として採用
    - このエクササイズの答えが全てではありませんが、実習に近い学習が可能

ほか、必要に応じて提示します。

### 1.6. その他

本資料のほか、講座資料置き場の[misc](../../misc)も参考として下さい。

また、初期の講座を終えた後に始めるプロジェクト演習では[Development](../../Development/)で必要と思われる予備知識の補充や初動について確認します。

## 2. JavaScript 概説

### 2.1. 歴史

一般にJavaScriptと呼ばれるプログラミング言語の歴史について簡単に現行規格に至るまでを概説します。

- [JavaScript History](http://www.slideshare.net/badatmath/js-shistory)

### 2.2. 言語の特徴

詳説は3章で行いますが、プログラミング言語JavaScriptは次のような特徴を持ち、C系プログラミング言語既習者には比較的とっつきやすいが、やや特異な仕様も持つプログラミング言語です。

- 動的型付け
- インタープリター
- プロトタイプベースOOP ← 特異

### 2.3. ECMAScript

歴史でも述べた様に現在一般にJavaScriptと呼ばれるプログラミング言語は ECMA-262 Edition 5.1th に基づいたものとなっています。

- 古代JavaScript → (標準化) → [ECMA-262](http://www.ecma-international.org/publications/standards/Ecma-262.htm)
    - 現行規格: ES-5.1 (≈ES-5)
    - ドラフト: ES-6

最近ではあまり使われなくなりつつありますが、JavaScriptの方言には以下の様なプログラミング言語もあります。

- [ActionScript](http://livedocs.adobe.com/flash/9.0_jp/ActionScriptLangRefV3/)
    - Adobe Flash とか Adobe Flex とか Adobe AIR とか
- [JScript](http://msdn.microsoft.com/ja-jp/library/cc427807.aspx)
    - Microsoft

また、ECMAScriptはプログラミング言語ですが、この中からオブジェクトを記述する部分だけを取り出して少しだけ厳密にしたものにJSONがあります。
JSONはデータ記述言語として現在世界中の多くの、JavaScriptとは全く関係の無い部分でも広く使われるに至りました。
また、JSONを元にしたスクリプト記述言語としてQMLなど関連性のある規格もJavaScriptとは独立して実用されています。

### 2.4. 処理系

- [V8](https://code.google.com/p/v8/)
    - Chromium に搭載された高速なJavaScriptエンジン
- [Node.js](http://nodejs.org/)
    - V8 を基にイベント駆動IOのネットワークプログラミングに適した環境を提供
    - [日本ユーザグループ](http://nodejs.jp/)もある
- [Rhino](https://developer.mozilla.org/ja/docs/Rhino)
    - Javaによる組み込み向けのJavaScriptエンジン
    - 「らいのー」と読んであげましょう
- [SpiderMonkey](https://developer.mozilla.org/ja/docs/SpiderMonkey)
    - この世界で最初のJavaScript処理系でFirefoxに受け継がれた

などなど。

## 3. ES5 基礎

### 3.1. 言語基礎

本節ではMDNの資料より、リファレンスとガイドを順に読み進めて解説します。この資料自体では1項目ですが、本講座の重要性の半分ほどを占めると言っても過言ではありません。実際、リンク先の資料のボリュームもそれなりにあります。

- [JavaScript リファレンス](https://developer.mozilla.org/ja/docs/JavaScript/Reference)
- [JavaScript ガイド](https://developer.mozilla.org/ja/docs/JavaScript/Guide)

途中、実際に小さなサンプルコードを多数紹介するので、各自Chromiumのコンソール（デベロッパーツール）またはNode.jsの対話シェルで実際に試しながら学習しましょう。

- Chromium
    - [詳説：デベロッパーツールの使い方](http://gihyo.jp/dev/feature/01/devtools/0001)
- [Node.js](http://nodejs.org/)
    - [Node.js 日本ユーザグループ](http://nodejs.jp/)

また、講座時間では毎回Codecademyを使った実習的な学習時間を設けるので怠らずに取り組みましょう。

- [Codecademy JavaScript](http://www.codecademy.com/)
    - アカウントを作成してログオンしておくと良い
    - 講座1回ごとに10%以上進められると良い

加えて、コード片のみならず、実際のソフトウェア開発では Node.js によるデバッギング環境、とりわけ node-inspector も役立つ事でしょう。必要に応じて使用して下さい。

- [node-inspector](https://github.com/dannycoates/node-inspector)
    - [SOURCEFORGE - はじめてのNode.js：Node.jsアプリケーションのデバッグ 3ページ](http://sourceforge.jp/magazine/13/04/16/080000/3)

### 3.2. 落とし穴

一通りのES3〜ES5レベルのJavaScriptに慣れたところで、JavaScriptについて復習しながらよくある落とし穴について把握して置きましょう。

- [JavaScriptの落とし穴](http://www.slideshare.net/ikdysfm/java-script-20131612)

## 4. 現状のJavaScript開発とES6

### 4.1. 状況把握

ES3→ES5でそれなりにまともになったとは言え、JavaScript開発、特に細々としたHTMLとCSSのビヘイビアの実装等に比較して中規模・大規模なJavaScriptの絡むソフトウェア開発はしんどい状況はさほど改善されていません。

かと言ってES4の頓挫から10年以上の長きに渡り失われてきたJavaScriptの発展となるES6はようやく2014年にドラフトを出す事になり現在必死に作成中で、SpiderMonkeyやV8が極一部の機能を試験的に実装し始めている程度に過ぎません。（まだ実用できる状況ではありません。）

#### 4.1.1. JavaScriptへのコンパイル

こうした状況のもとに近年は「JavaScriptへのコンパイラー」やその機能を主とした新言語が乱立する事態となっています。
差し当たり資料を掻い摘んで紹介します。

- [ちゃんとWeb会議スライド『Coffee script』](http://www.slideshare.net/taniguchimakoto/webcoffee-script)
    - [CoffeeScript](http://coffeescript.org/)

- [JSX / Haxe / TypeScript](http://www.slideshare.net/bleistift/jsx-haxe-typescript)
    - [JSX](http://jsx.github.io/)
    - [Haxe](http://haxe.org/)
    - [TypeScript](http://www.typescriptlang.org/)

GoogleからDartなんて処理系も出現しました。

- [Introduction to dart](http://www.slideshare.net/yohanbeschi/introduction-to-dart)
    - [Dart](http://www.dartlang.org/)

C++からJavaScript(with HTML5)へのコンパイルもEmscriptenによりほぼ実用化されています。

- [C++ on the Web: Run your big 3D game in the browser](http://www.slideshare.net/andreweissflog3/quovadis2013-cpp-ontheweb)
    - [Emscripten](http://emscripten.org/)
        - [LLVM](http://llvm.org/)

#### 4.1.2. ES6

もちろん、やがて来るES6時代。クラスベースOOP、非同期APIの大幅な強化、簡潔に記述できるラムダ式・機能的になったパラメーターなどの構文、列挙とfor-of、function\*とyieldなどなどの言語としての仕様が大幅に強化されます。
当然上記した各種の処理系も追随するか、或いは既に言語機能として持っているものも含まれています。

- [ECMA-262 Edition 6 Draft Specification](http://wiki.ecmascript.org/doku.php?id=harmony:specification_drafts)
    - 言語仕様書（草案）
- [es6-shim](https://github.com/paulmillr/es6-shim)
    - 既存処理系にES6互換性をライブラリーレベルで可能な限り拡張

来年くらいには下記の表もGREENが増えている事を期待したいですね。

- [ECMAScript 6 compatibility table](http://kangax.github.io/es5-compat-table/es6/)
    - 参考: [ECMAScript 5 compatibility table](http://kangax.github.io/es5-compat-table/)

今すぐ使える武器は勿論重宝しますが、ES6もそろそろある程度は可能な部分から触れ始めて置くと良いでしょう。

### 4.2. 既存資源

ES5レベル現在でも豊富なライブラリー・フレームワーク・ツール群が開発に役立てられています。
幾つか、特に見た目や機能的に面白いものを中心に抜粋して紹介します。

- [Three.js](http://threejs.org/)
- [Physics](http://jonobr1.github.io/Physics/)
- [Box2DJS](http://box2d-js.sourceforge.net/index2.html)
- [Enchant.js](http://enchantjs.com/)
- [jQuery](http://jquery.com/)
- [yui](http://yuilibrary.com/)
- [Underscore.js](http://underscorejs.org/)
- [Pot.js](http://polygonplanet.github.io/Pot.js/)
- [Meteor](http://meteor.com)
- [express](http://expressjs.com/)

ES5あるいはES3レベルに準拠した現実に今すぐ使える様々なライブラリーが、このほかにも大小・多数・大量に現存します。
有効に活用すると良いでしょう。

注意点として、こうしたライブラリーはECMA-262の純粋な言語仕様だけでなく、多くの場合処理系の実装やプラットフォームの規格に依存している点が挙げられます。
例えば、プラットフォームの規格としては[HTML5(WebGL、WebAudio、DOMなどのAPI)](http://www.w3.org/html/wg/drafts/html/master/)、処理系としては[Node.js固有のAPI](http://nodejs.jp/nodejs.org_ja/api/)など。

## 5. 課題

本講座の成績評価の6割は10月末（予定）時点でのこの課題の成果状況の評価によって行います。

本講座で基礎的なES5レベルのJavaScriptを習得した後に、開発チームを編成し、要件定義、設計、仕様書作成、プロジェクトマネージメント、オープンソースソフトウェア開発、チケット駆動開発を実践し、課題の制作と提出を行なって貰います。

本講座で開発した成果から学習成果発表会等へまっしぐらするチームもあり得ます。

また、講座時間中に発表の機会を3回設けます。
チームごとに自分たちの取り組み内容を全体にプレゼンテーションしながら進めます。

- 発表
    1. 企画プレゼンテーション (5月)
        - メンバーと企画概要の紹介と中間・最終プレゼンテーションまでの計画
    1. 中間プレゼンテーション (夏休み前)
        - 要素技術とプロジェクトの現状及び最終プレゼンテーションまでの計画
    1. 最終プレゼンテーション (10月)
        - メンバー・企画概要・要素技術・製品デモ・プロジェクトの総括

注意点
    - プレゼンテーション資料に著作権を侵害したりライセンス違反を犯す要素を含めない事。
        - 素材を使うなという訳では無く、正しくかつ効果的に使用しましょう。

必要な予備知識やプロジェクトの初動については[Development](../../Development)を参照して下さい。

### 5.1. 選択肢

課題とする開発技術として次の中から1つ、開発する企画として1つを撰び、その組み合わせでプロジェクトを進めます。

受講者が多い場合は選択肢の重複を含め再考します。

#### 5.1.1. 開発技術

以下の何れかから他のチームと被らない様に1つ選んで採用する。

1. TypeScript
    - ES5の上位互換を標榜するES6にも近い言語
1. Haxe
    - 実はそれなりに歴史もあり、JavaScript以外にも使いようが広い
1. JSX
    - 翻訳後のJavaScriptの実行速度に重点を置いている
1. Dart
    - やや特異な点も多いが環境も整備されおりそれなりに楽しめるかも
1. CoffeeScript
    - ES5の痒いところに手が伸びる
1. ES6
    - shimも含め現状対応可能な範囲で
1. emscripten
    - 他の選択肢に比べ難易度が明らかに高く、この選択肢はチームに十分な開発力があると先生が確認できる場合に限ります

実際のところはJavaScriptレベルでは相互にリンクして使用する事もできるが、本講座の課題ではJavaScript処理系にはここで決めたどれか1つの要素技術のみから生成したJavaScriptコードを用いる事とします。

#### 5.1.2.

以下の何れかから他のチームと被らない様に決定する（恐らくこれはチーム編成の後にほぼ先着順の様な形で決める）。

1. ロードモナークっぽい箱庭ゲーム
1. レミングスっぽいパズルアクションゲーム
1. ザルバールの蒸留塔っぽいパズルアクションゲーム
1. チーム独自の企画
    - チーム内でまとまった企画案をチーム編成を行った回の次の講座時間までに提案し承認を得られる場合に限ります。

- 注意
    - 以上に挙げた具体的なゲームソフトウェアの名称はイメージとしての参考資料とし、基本的には丸パクリではなく自分たちで企画・要件を面白くかつ納期を考慮して現実的な落とし所に整理して取り組みましょう。

### 5.2. いわゆるフリー素材やライブラリー等の利用について

いわゆるフリー素材等は大いに利用して構いません。

但し、リポジトリーに含めて配布しても良いか、利用するにあたって守らなければならない条件、つまりライセンスに問題は無いか確認し、原則としてREADMEやマニュアルにはチーム外部から取り込んだ全ての著作物についての一覧を掲載して下さい。
ライセンスを正しく守って利用している素材については効果的な利用に対して加点する事はあれど減点する事はありません。

また、ライブラリーについても大いに利用して構いません。
寧ろ積極的に利用して下さい。

但し、ライブラリーについてもライセンスに十分注意し、原則としてREADMEやマニュアルに使用したライブラリーの一覧を掲載して下さい。

他に、フリー素材やライブラリーで無くとも、開発にあたり参考とした情報、役だった情報などがあればREADMEで謝辞と共に紹介して下さい。

### 5.3. 評価方法

講座終了時点で以下の基準から決定します。

- 総評 ( unorm \[0.0-1.0\] )
    - 授業態度 (個人評価点 0.40 )
        - 講義への参加姿勢
        - プロジェクトへの貢献度
            - サブPMとして上手くプロジェクトを管理している
            - 多くのまたは難しいIssueを熟している
    - 課題評価 (チーム評価点 0.60 )
        - 仕様書の完成度
        - GitHub Issuesの活用具合
        - Gitのコミットログや開発ブランチの活用具合
        - ソースコードの美しさ
        - 製品の完成度
        - README・ユーザーマニュアル・プロモーションサイトの分かり易さ
            - READMEが整備されていない場合は大幅な減点を行う
            - 使用した素材やライブラリーのライセンスに従った記述が欠落している場合は0点もあり得る
            - マニュアル・プロモサイトは必須ではないので余裕があれば用意すると良い
        - プロジェクトや製品の面白さ

## 6. 連絡等

本項は講座の直接の受講者を対象としたものです。この資料は公開していますが、直接の受講者以外の方からのご連絡には対応致しかねる場合が御座います。ご了承下さい。

### メーリングリスト

講座に関する諸連絡はメーリングリストで行います。
初回の講座で案内しますので受講者は必ず登録して下さい。

- [Google Groups / wrp-lectures-javascript](https://groups.google.com/forum/?fromgroups#!forum/wrp-lectures-javascript-2013)
    - <wrp-lectures-javascript-2013@googlegloups.com>

- 連絡がある場合は基本的にこのメーリングリストを用いて下さい。
- 講座に関連した質疑応答やディスカッションにも活用して構いません。
    - チーム開発を進めている場合、連絡が可能な場合はチームの他のメンバー遅への配慮として遅刻や欠席については連絡する事をお勧めします。
    - 遅刻や欠席それ自体は自分の人生と相談して適宜に判断して行動して下さい。

### 担当指導教員 @usagi への直接連絡が必要な場合

- <usagi@WonderRabbitProject.net>
    - 送信する時間帯に気を使う必要は全くありません。用事があれば即座にメールして下さい。
    - 初めて連絡する場合を除き、所属や氏名をビジネスメールよろしく冗長に記載する必要はありません。
    - 「ご査収下さい」などの表現を無理に使う必要もありません。もしあなたが先生を多少なりとも尊敬してくれるとすればそれはとても嬉しい事ですが、私へのメールでは礼儀と丁寧さは必要最小限に留め、要件を明確に伝える事に重点を置いて頂いた方が有り難いです。

※Facebook、Twitter、Google+等で見つけてフォローして頂くのは自由ですが、それらは個人的な付き合いか、共通の趣味などが無ければこちらからアクションする事はたぶんありません。悪しからず。

※C++erとVimmerはだいたい歓迎します。茶人も歓迎します。

----

Copyright &copy; 2013 Usagi Ito.
License: [GNU FDL-1.3](http://www.gnu.org/licenses/fdl-1.3.html)

