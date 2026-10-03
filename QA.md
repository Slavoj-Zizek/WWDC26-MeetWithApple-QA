# Slido Q&A — Meet with Apple（対面形式 / in person）

> Meet with Apple「[次なる可能性：WWDC26発の注目の最新アップデート（対面形式）](https://developer.apple.com/events/view/U828YY6DYC/dashboard)」当日の Slido 質疑応答
>
> Slido Q&A from Meet with Apple, “[What’s next: highlighted updates from WWDC26 (in person)](https://developer.apple.com/events/view/U828YY6DYC/dashboard)”. The English title is a translation of the Japanese event name. The official English title was not confirmed.
>
> 最終更新 / Last updated: 2026-07-02（全7弾・計68件 / 7 parts, 68 items）
>
> 日本語が原文です。各見出し・発言の下の *斜体* が英語訳です。もとから英語の質問と回答はそのまま残しています。英語は聞き取りメモの訳であり、公式発表ではありません。
>
> Japanese is the source. *Italic* text under each heading and remark is an English translation. Questions and answers that were originally in English are left as written. The English is a translation of these notes, not an official statement.

---

## Apple Intelligence / Foundation Models / Siri

### AI モデルの選択（Apple Intelligence と ChatGPT）

*Choosing an AI model (Apple Intelligence and ChatGPT)*

**質問**（Anonymous）

> 今まで、Apple IntelligenceとChatGPTの連携はユーザー側ができました。そのようにユーザー側がApple Intelligenceを自分のコントロール下のaiモデルを選ぶようなイメージはありますか

*Until now, users could connect Apple Intelligence with ChatGPT. Is the idea that users would similarly choose, under their own control, which AI model Apple Intelligence uses?*

**回答**（Shun）

> OS27シリーズにおいては、Image Playgroundなどでは引き続きChatGPTとの連携はのこってますが、Siri AIの中にはボタンなどは残っておりません。Apple Intelligence自体は、Apple Foundation Modelsという独自のモデルから今のところ変更できる機能はないため、個別にChatGPTのアプリなどを入れていただく必要があるなどがあります。

*On the OS 27 series, integration with ChatGPT remains in places such as Image Playground, but there is no longer a button for it inside Siri AI. Apple Intelligence itself currently has no way to switch away from Apple’s own Apple Foundation Models, so you need to install something like the ChatGPT app separately.*

---

### iOS 27 以降の 3rd party AI と Siri（ChatGPT 代替・App Schema）

*Third-party AI and Siri from iOS 27 on (ChatGPT as a substitute, App Schema)*

**質問**（Anonymous）

> Siriに聞く代わりにChatGPT等3rd party AIで代替する機能がiOS 26まではついていたと思うんですがiOS 27以降はどのような扱いになるのでしょうか？「3rdもAppSchemaの連携はできるのか？」「Siri AIが行えるような操作も3rdは使えるのか？」

*Up through iOS 26, I believe there was a feature to use a third-party AI such as ChatGPT instead of asking Siri. How is that treated from iOS 27 on? “Can third parties also integrate via App Schema?” “Can third parties also perform the kinds of actions Siri AI can?”*

**回答**（Shun）

> ChatGPT に聞くという提示なくなりました。Siri AIがPrivate Cloud Computeをつかって答えてくれます。また、Siri AIに対して必要であればChatGPTで聞きたとリクエストすれば、ChatGPTのクライアントアプリを立ち上げたりはできます。

*The prompt to ask ChatGPT is gone. Siri AI answers using Private Cloud Compute. If you ask Siri AI to ask ChatGPT when you need to, it can launch the ChatGPT client app.*

**回答**（Shun）

> 3rd party もApp Schemaを導入できますし、それによってSiri AIから呼び出せます。Siri AIが行えるような操作は直接3rd partyからはできません。Foundation models frameworkなどを使ってアプリ内の機能で似たような実装を検討いただく必要があります。ただし、あくまでのアプリ内の機能に限り、他のアプリの連携などはできません。

*Third parties can adopt App Schema, and Siri AI can call them through it. The kinds of actions Siri AI itself performs cannot be done directly by a third party. You need to consider a similar implementation as a feature inside your app, using the Foundation Models framework and so on. That is limited to features inside your own app. You cannot integrate with other apps.*

---

### Foundation Models の出力品質（要約・フォーマット）

*Foundation Models output quality (summaries and formatting)*

**質問**（Ichiro Hirata）

> Foundation Modelsに当月の収支や資産状況を要約させると、文法的に少し不自然だったり、2〜3文にまとめるよう指示をしても、急に箇条書きになったものを出力したりします。確実な出力には、やはりテンプレートを複数用意したり、フォールバック処理を入れるなどが必要でしょうか？適切な対応方法があればご教示いただきたく。

*When I have Foundation Models summarize this month’s income and expenses or asset status, the grammar is a bit unnatural, or it suddenly outputs a bulleted list even when I ask it to keep the summary to two or three sentences. For reliable output, do we still need several templates and fallback handling? If there is a good approach, please share it.*

**回答**（Shun）

> オンデバイスのモデルですが、サンプルの文章を入れて頂けると、比較的アウトプットが改善される傾向があります。ただ、サンプル文は使うなと明確に指示を追記しておくことも必要です。そうでないと、サンプル文章に近いものを出してしまうことがあります。

*It is an on-device model, but including sample sentences tends to improve the output. You also need to explicitly instruct it not to use the sample text. Otherwise it may produce something close to the sample.*

---

### Evaluations Framework の画像入出力

*Image input and output in the Evaluations Framework*

**質問**（Anonymous）👍 3

> evaluation framework のインプット　アウトプットに画像は加わる予定でしょうか？？

*Is there a plan to add images to the input and output of the evaluation framework?*

**回答**（Shun）

> Foundation models framework自体では画像の入力は受け付けますが、生成結果はすべてテキストまたは@GenerableによるStructでの出力となるため、Evaluations Frameworkとして今のところインプット・アウトプットで画像は使えません。ぜひ、他のLLMのケースも踏まえて、使っていけるといいといいことでしたら、是非 http://feedbackassistant.apple.com/へご要望いただけると幸いです。

*The Foundation Models framework itself accepts image input, but generated results are all text, or structs produced with `@Generable`. So the Evaluations Framework cannot use images for input or output at this time. If, taking other LLM cases into account as well, you would like to be able to use them, please file a request at http://feedbackassistant.apple.com/.*

---

### Foundation Models の画像入力（対応デバイス・API）

*Image input in Foundation Models (supported devices and APIs)*

**質問**（treastrain / Tanaka.R）👍 7

> Foundation Models について画像の入力ができるようになったという話がありましたが、Apple Intelligence が使える iOS 27 の全てのデバイスで画像の入力ができますか。もし対象外のデバイスがある場合、それを判別できる API はありますか。

*I heard Foundation Models can now take image input. Can every iOS 27 device that supports Apple Intelligence take image input? If some devices are excluded, is there an API to detect that?*

**回答**（Shun）

> Apple Intelligence が対応している機種であれば画像入力はすべて使えます。ただし、iPhone 17 Pro, iPhone Air といったデバイスは導入されているモデルがより高度なものになっているので、生成結果などが異なる可能性があります。

*Image input is available on every model that supports Apple Intelligence. Devices such as iPhone 17 Pro and iPhone Air have a more advanced model installed, so generated results may differ.*

**フォローアップ**（treastrain / Tanaka.R）

> ありがとうございます！

*Thank you!*

---

### Siri AI の日本語対応（音声・テキスト）

*Japanese support in Siri AI (voice and text)*

**質問**（Anonymous）👍 15

> Siriの通知読み上げを使用していますが、日本語の読み上げがひどいなと感じています（漢字で表記されている名前を正しく読めなかったり、英単語をアルファベットで読み上げたり）。日本語のアプリでも十分に動くのでしょうか？

*I use Siri’s notification readout, and the Japanese readout feels poor. It misreads names written in kanji, and reads English words letter by letter. Will it work well enough for Japanese apps too?*

**回答**（Shun）

> Siri AIについては音声での対応は現在、英語（US）のみとなっております。今後の言語対応についてはまだ未定となっておりますので、今後のアナウンスをお待ちください。なお、文字でのTypeによるリクエストについては日本語でもベータ版においてある程度動作いたしますので、ベータ版でどの程度連携できるかご確認いただければと思います。

*For Siri AI, voice support is currently English (US) only. Future language support is still undecided, so please wait for a later announcement. Typed requests do work to some extent in Japanese in the beta, so please check in the beta how well the integration works.*

---

### Private Cloud Compute（PCC）と個人情報

*Private Cloud Compute (PCC) and personal information*

**質問**（akkey）👍 8

> 「ユーザの個人情報はPCCに渡すべきではない」のようなルールはありますか？

*Is there a rule along the lines of “a user’s personal information should not be sent to PCC”?*

**回答**（Anonymous）

> データが処理された後は削除されること、またご利用されている方以外がそこ環境にアクセスされないこと、また処理に使ったデータをモデル学習等に使わないという環境がPrivate Cloud Computeになってますので、オンデバイスとほぼ同等の環境として利用いただけますので、個人情報を渡してはいけないということはありません。

*After data is processed it is deleted, no one other than the person using it can access that environment, and data used for processing is not used for model training. That is what Private Cloud Compute is, so you can treat it as nearly equivalent to on-device. It is not the case that you must not pass personal information.*

**回答**（Shun）

> https://security.apple.com/blog/expanding-pcc/ 詳しい環境についてはこちらの記事などをご確認ください。

*See this article for details of the environment: https://security.apple.com/blog/expanding-pcc/*

---

### PCC の利用資格（200万ダウンロード制限）

*Eligibility for PCC (the 2-million-download limit)*

**質問**（Anonymous）

> Private Cloud Compute は200万ダウンロード以下の開発者しか使えないとのことですが、1アプリにつき200万ダウンロードでしょうか。developerアカウントの全てのアプリを合算しての200万ダウンロードでしょうか。

*I heard only developers under 2 million downloads can use Private Cloud Compute. Is that 2 million downloads per app, or 2 million downloads added up across every app on the developer account?*

**回答**（Shun）

> https://developer.apple.com/private-cloud-compute/

*See https://developer.apple.com/private-cloud-compute/*

**回答**（Shun）

> Have fewer than 2 million first-time app downloads from any of their apps on the App Store. アカウント内で1つのアプリでも200万初回ダウンロードが超えると、そのアカウント内で利用ができなくなります。

*“Have fewer than 2 million first-time app downloads from any of their apps on the App Store.” If even one app in the account exceeds 2 million first-time downloads, PCC can no longer be used within that account.*

**回答**（Shun）

> なお、6ヶ月間の猶予期間はあるようですが、初期の段階から、fallbackの仕組みでオンデバイスや他のLLMに流すなどは実装いただくと良いかと思います。

*There appears to be a six-month grace period, but it would be good to implement a fallback from an early stage that routes requests to on-device or another LLM.*

---

### PCC 一般開放の目処

*Timeline for general availability of PCC*

**質問**（Anonymous）👍 4

> PCC一般開放の目処はございますか？？

*Is there a timeline for opening PCC to everyone?*

**回答**（Shun）

> 今の段階で今後の展開はきまっておりません。ぜひご希望あれば、http://feedbackassistant.apple.com/に利用ケースなどを記載のうえ、登録いただけますと幸いです。

*Future rollout has not been decided at this stage. If you have a request, please describe your use case and submit it at http://feedbackassistant.apple.com/.*

---

### 日本語ローカライズ（入力・Foundation Models）

*Japanese localization (text input and Foundation Models)*

**質問**（Anonymous）

> 近年、文字入力やSiriを使用時に日本語への理解度が落ちているような印象を受けます。Apple IntelligenceやFoundation Modelsでの日本語ローカライズは十分に行われている認識でしょうか？

*In recent years I get the impression that Japanese comprehension has declined when using text input or Siri. Is Japanese localization for Apple Intelligence and Foundation Models considered sufficient?*

**回答**（Shun）

> iOS27/macOS27において、日本語入力について改善が行われておりますので、是非ベータ版でお試しください。Apple IntelligenceやApple Foundation Modelsの日本語対応も行われております。

*Japanese input has been improved in iOS 27 and macOS 27, so please try the beta. Japanese support for Apple Intelligence and Apple Foundation Models is also in place.*

---

### Apple Foundation Models の学習データ（Swift コードベース等）

*Training data for Apple Foundation Models (Swift codebase and similar)*

**質問**（Daniil Surnin）

> Do Apple train foundation models on their own swift codebase? Swift Forum, documentation?

*Original question is in English.*

**回答**（Shun）

> https://machinelearning.apple.com/research/introducing-third-generation-of-apple-foundation-models
>
> what we can answer about Apple Foundation Models is based on blog from our machine learning team. could you plz take a look on those blogs?

*Original answer is in English. The link is the machine-learning team’s blog on the third generation of Apple Foundation Models.*

---

### Mac で最大・最高性能の Foundation Models を動かす条件

*Requirements to run the largest, highest-performance Foundation Models on a Mac*

**質問**（Daniil Surnin）

> How can I run the most performant and largest foundation models on my Mac?

*Original question is in English.*

**回答**（Shun）

> Mac with M3 and later with 12GB or more in memory is criteria to run AFM 3 Core Advanced. and you need to install macOS 27 beta on those machine.

*Original answer is in English.*

---

### Siri AI の商用日本語化スケジュール

*Schedule for Japanese Siri AI in production*

**質問**（Anonymous）

> 商用環境での「Siri AI」の日本語化は、いつ頃リリース予定となりますでしょうか？

*About when is Japanese support for “Siri AI” scheduled to ship in a production environment?*

**回答**（Shun）

> まだ正式なアナウンスがでておりませんの、正式なアナウンスをお待ちいただければと思っております。今の段階で発表されている内容は、秋のOSリリースの段階で英語(US)があるということのみとなっております。

*There is no official announcement yet, so please wait for one. What has been announced at this stage is only that English (US) will be available with the fall OS release.*

---

### Siri AI の画面読み取り範囲（スクロール外）

*How much of the screen Siri AI reads (content outside the scroll viewport)*

**質問**（zunda）

> 画面上のコンテンツをSiri AIが読んでくれるとのことですが、スクロールする画面で下の方に表示されていない部分も読み取ってくれるでしょうか？

*I heard Siri AI can read on-screen content. On a scrolling screen, will it also read parts farther down that are not currently shown?*

**回答**（Shun）

> 基本的に画面の中で表示されている範囲のもののみが対象になります。

*In principle, only what is currently visible on screen is in scope.*

---

### Siri AI と Generative UI（アプリ不要の未来？）

*Siri AI and Generative UI (a future without opening apps?)*

**質問**（zunda）

> iOS 27のSiri AIでは、Siri AIアプリ内で、Generative UIのようなものが作れると考えています。今後Siri AIの中だけで完結するようなUIも作れなくはないと考えています。今後のユーザー体験としてAppleのデザイン(設計)方針としてどのようになっていく、なっていくのが良いと考えていますでしょうか？ユーザーが個別のアプリは開かなくなる未来もあるのかなと思い質問させていただきました。

*I think Siri AI on iOS 27 can create something like Generative UI inside the Siri AI app, and that it is not impossible to build UI that is completed entirely inside Siri AI. As a future user experience, what do you think Apple’s design direction will be, or should be? I asked because I wonder whether users might stop opening individual apps.*

**回答**（Shun）

> 日頃繰り返し行うような処理はSiriで対応しつつも、詳細な設定や普段あまりしない作業などはアプリを起動していただいてといった流れが今の段階では現実的な棲み分けかなと考えています。ただし、長期的な観点でこの棲み分け自体は変わっていくこともありますので、また定期的にAppleのイベントやセッションなどにご参加いただいてキャッチアップいただけますと幸いです。

*A realistic split at this stage is to handle things people repeat day to day with Siri, and to launch an app for detailed settings and tasks they rarely do. Over the long term that split itself may change, so please keep catching up by joining Apple events and sessions regularly.*

---

### App Intents 連携のパフォーマンス影響

*Performance impact of App Intents integration*

**質問**（Anonymous）

> 自分のアプリにSiriの機能を組み込んだ場合、ユーザーの現在のiOS、ハードのスペックなどでアプリの動作が重くなったりする？

*If I build Siri features into my app, could the app become heavier depending on the user’s current iOS version or hardware specs?*

**回答**（Shun）

> 特に皆さんのアプリにApp IntentフレームワークをとりいてSiriとの連携をおこなったとしても、それ自体によって大きなパフォーマンスへの影響はないかと思います。

*Even if you adopt the App Intents framework in your app and integrate with Siri, that itself should not have a large performance impact.*

---

### カスタム App Schema

*Custom App Schema*

**質問**（you）

> App schema で定義されているものに当てはまらないEntityの場合カスタムのapp schemaを定義することで、その性質をSiriに伝えることはできますか？

*If an entity does not fit what App Schema already defines, can I define a custom app schema and convey what it is to Siri?*

**回答**（Shun）

> 今現在カスタムのApp Schemaを作ることができないため、既存のもので該当するものがない場合は、http://feedbackassistant.apple.com/ へご要望登録いただけますと幸いです

*You cannot create a custom App Schema at this time. If nothing existing fits, please file a request at http://feedbackassistant.apple.com/.*

---

### App Schema Domains の今後の拡充

*Future expansion of App Schema domains*

**質問**（Anonymous）👍 5

> App schema domainsは今後増えていきますか？

*Will App Schema domains increase in the future?*

**回答**（Shun）

> 是非http://feedbackassistant.apple.com/ にこんなApp Schema Domainsが欲しいというリクエストがありましたら登録ください。

*If there are App Schema domains you want, please submit that request at http://feedbackassistant.apple.com/.*

---

### App Schema の独自定義（ゲームクエスト等）

*Defining your own App Schema (game quests and similar)*

**質問**（Anonymous）👍 4

> スキーマは自分で定義することはできるでしょうか。例えば、ゲームのクエストなになにをクリアして、みたいなスキーマがあると面白いと思いました。

*Can we define schemas ourselves? For example, I thought a schema like “clear such-and-such game quest” would be interesting.*

**回答**（Shun）

> App Schema はすべてApple側で管理するものとなっております。お手数ですが、http://feedbackassistant.apple.com/へご希望のApp Schemaを利用シーンを添えて記載いただけると大変ありがたいです。

*App Schema is entirely managed by Apple. Please describe the App Schema you want, along with the use case, at http://feedbackassistant.apple.com/.*

---

### 複数アプリで同一 Entity の判別（Donations）

*Telling apart the same entity across multiple apps (donations)*

**質問**（Anonymous）

> 複数のアプリで同じエンティティを持っていた場合、Siriはどのアプリのエンティティを指しているのか判別できないでしょうか？

*If several apps have the same entity, can Siri not tell which app’s entity is meant?*

**回答**（Shun）

> ドネーションという機能を使うことで、SiriからどちらのアプリのEntityを優先するべきかの学習させることができます。
>
> https://developer.apple.com/jp/videos/play/wwdc2026/343?time=370
>
> 是非こちらをご確認ください。

*By using a feature called donation, you can teach Siri which app’s entity it should prefer. See https://developer.apple.com/jp/videos/play/wwdc2026/343?time=370.*

---

### Siri の学習（メッセージアプリ選択・Intent Donations）

*How Siri learns (choosing a messaging app, intent donations)*

**質問**（Anonymous）👍 1

> 聞き逃していたら申し訳ないのですが、Siriが学習してどのメッセージアプリを使うかを判断できるようになるという話がありましたが、学習のためにはSiriが想定と違うメッセージアプリを使おうとするのを訂正するというステップが必要でしょうか？それとも普段のアプリ使用を監視して学習をしてくれているのでしょうか？

*Sorry if I missed this. I heard Siri can learn and decide which messaging app to use. For that learning, do we need a step where we correct Siri when it tries to use a messaging app we did not expect? Or does it learn by watching ordinary app use?*

**回答**（Shun）

> 不正が疑われるようなドネーションについてはSiri側で検知して影響が出ないようにする仕組みがあるので、皆さんのアプリ内ではボタンタップしたときにドネーションするなど、最低限かつ必要な実装だけしていただければ、特に訂正とかしていただくAPIもないため、何か対応は必要ありません

*Siri has a mechanism that detects donations that look suspicious and keeps them from having an effect. In your app, if you donate when the user taps a button and implement only the minimum that is needed, there is no API for making corrections, so no extra handling is required.*

---

### Donation のデータ量制限

*Limits on how much data a donation can include*

**質問**（Anonymous）👍 3

> Donationにデータを渡したもの勝ちみたいなことになりそうなのですが、渡す量の制限などはありますか？

*It seems like whoever passes more data into a donation wins. Are there limits on how much you can pass?*

**回答**（Shun）

> （別にも同様の質問があったため、同じ回答をさせていただきます。ご了承ください）
>
> 過剰なドネーションなどについては、除外される仕組み等もあります。ユーザーの通常アクション（例えばボタンタップなど）にともなった、Donationといった自然な登録の範囲であれば、正しくカウントされていきます。

*The same question came up elsewhere, so this is the same answer. Excessive donations can be excluded. Donations that stay within a natural range and accompany an ordinary user action, such as a button tap, are counted correctly.*

---

### Donation で渡すべき情報の種類

*What kind of information to pass in a donation*

**質問**（Anonymous）

> ドネーションでAppから渡せる情報(渡すと良い情報)はどのようなものがありますか？App内で特定の時間に何か特別な行動をとったログ(新宿付近でアプリを開いて何かを買った)とかをイメージしてますが、解釈合ってますでしょうか

*What kinds of information can an app pass in a donation, and what is good to pass? I’m picturing a log of a special action at a specific time inside the app, such as opening the app near Shinjuku and buying something. Is that the right interpretation?*

**回答**（Shun）

> Siriから呼び出すためのAppSchemaを紐づけたIntentやEntityなどについては、できる限りDonationしていただくことをお勧めします。他のアプリで同じAppSchemaがあった場合、どちらのアプリを呼び出すべきかはDonationの度合いによって異なってきます。

*For intents and entities tied to an App Schema so Siri can call them, we recommend donating as much as you can. If another app has the same App Schema, which app should be invoked depends on how much has been donated.*

**回答**（Shun）

> https://developer.apple.com/documentation/appintents/donating-your-apps-data-and-actions-to-the-system#Suggest-relevant-actions-and-data-from-your-app

*See https://developer.apple.com/documentation/appintents/donating-your-apps-data-and-actions-to-the-system#Suggest-relevant-actions-and-data-from-your-app*

**回答**（Shun）

> https://developer.apple.com/jp/videos/play/wwdc2022/343?time=365

*See https://developer.apple.com/jp/videos/play/wwdc2022/343?time=365*

---

### Siri による Donation の真贋判定

*How Siri judges whether a donation is genuine*

**質問**（Anonymous）👍 4

> SiriのほうはAppからのドネーションの真贋をどのように判定しますか？

*How does Siri judge whether a donation from an app is genuine?*

**回答**（Shun）

> 過剰なドネーションなどについては、除外される仕組み等もあります。ユーザーの通常アクション（例えばボタンタップなど）にともなった、Donationといった自然な登録の範囲であれば、正しくカウントされていきます。

*Excessive donations can be excluded. Donations that stay within a natural range and accompany an ordinary user action, such as a button tap, are counted correctly.*

---

### ユーザー趣味嗜好の Intent 蓄積とプライバシー

*Storing intents about user tastes, and privacy*

**質問**（Anonymous）👍 3

> 自分のアプリにユーザーの趣味嗜好をintentとしてデータを蓄積できるか？プライバシーの事前の許可は？

*Can my app accumulate data about the user’s tastes and preferences as intents? Is prior privacy permission required?*

**回答**（Shun）

> 各アプリからDonationされたIntentについてはOS側で管理されているため、アプリ側から取得などはできません。プライバシーの懸念等もありますが、もし取得できることでアプリの機能として役にたつなど想定がありましたら、是非 http://feedbackassistant.apple.com/ へ登録いただけますと幸いです。

*Intents donated from each app are managed by the OS, so the app cannot retrieve them. There are privacy concerns as well. If you can imagine that being able to retrieve them would help as an app feature, please submit that at http://feedbackassistant.apple.com/.*

---

### サードパーティアプリと Siri のマルチターン

*Multi-turn conversations between third-party apps and Siri*

**質問**（Anonymous）👍 2

> サードパーティアプリは新しい Siri とマルチターンでの会話はできるのでしょうか？それとも単発アクションのみ？

*Can third-party apps have multi-turn conversations with the new Siri, or only one-shot actions?*

**回答**（Shun）

> Siri AIアプリの中であれば、マルチターンで利用いただけますし、また、音声やTypeでホームスクリーン等から利用した場合も、App Intent の実装方法によってマルチターンにしていくこともできます。

*Inside the Siri AI app, you can use multi-turn. When the user speaks or types from the Home Screen and elsewhere, you can also make the interaction multi-turn depending on how you implement App Intents.*

---

### Siri AI の学習データとプライバシー

*Training data for Siri AI, and privacy*

**質問**（Takuma）👍 2

> Siri AIへの学習させるためのデータはどのようなデータを入れるのでしょうか？ユーザーのプライバシー情報につながる情報もあるかと思いますが、セキュリティやプライバシーは保護されるのでしょうか？

*What kind of data is put in to train Siri AI? Some of it may lead to users’ private information. Are security and privacy protected?*

**回答**（Shun）

> Siriに関連する処理は基本的にオンデバイスまたはPCCでの処理となりますので、セキュリティ・プライバシー自体は担保されております。学習という観点ではApp IntentのDonationが皆さんのアプリから行なっていただけるものになっておりますが、基本的にそこには個人情報などは含まれておりません。

*Processing related to Siri is basically on-device or on PCC, so security and privacy themselves are assured. From a learning standpoint, what your apps can provide is App Intent donations, and those basically do not include personal information.*

**回答**（Shun）

> https://developer.apple.com/jp/videos/play/wwdc2024/343?time=370　是非こちらもご確認ください。

*Please also see https://developer.apple.com/jp/videos/play/wwdc2024/343?time=370.*

---

### `system.search` の動作

*How `system.search` behaves*

**質問**（zunda）👍 1

> `system.search`を登録(開発)すると、アプリ内コンテンツ検索をSiriなどが使ってくれるという理解であっていますでしょうか？

*If I register (develop) `system.search`, is it correct that Siri and others will use in-app content search?*

**回答**（Shun）

> 利用者の方がSiriに対して、依頼した探したいものをKeywordとして、アプリ内のサーチ機能に伝達してくれる機能となってます。そのためSiriがサーチをするのではなく、アプリを起動して検索結果を起動するというのが期待される動作になります。

*It passes what the user asked Siri to find, as keywords, to the search feature inside the app. The expected behavior is not that Siri searches itself, but that it launches the app and opens the search results.*

---

### AI 全体の日本語対応・精度（横断）

*Japanese support and accuracy across AI features*

**質問**（Anonymous）👍 1

> 全体的に、AIを製品全体へ組み込んでいく発表が多かった印象です。日本語で利用する前提だと、日本語でいつ使えるようになるのか、回答精度はどの程度か、など気になります。

*Overall, I got the impression there were many announcements about building AI into the whole product. Assuming use in Japanese, I wonder when it will be usable in Japanese, and how accurate the answers will be.*

**回答**（Shun）

> Foundation Models framework については、日本語での利用は問題なくできます。精度については入力するプロンプトやToolの設定などによって改善できますので、実装次第かなと思います。またSiri AIについては音声は英語（US）のみの対応となっており、日本語対応の時期は未定となっております。ただ今後展開される予定ではあります。また、Siri AIについては、文字での入力・操作はベータ版で利用できますので是非お試しください。

*The Foundation Models framework can be used in Japanese without a problem. Accuracy can be improved by the prompts you pass and by tool settings, so it depends on the implementation. For Siri AI, voice is English (US) only, and the timing of Japanese support is undecided, though expansion is planned. Typed input and control for Siri AI are available in the beta, so please try them.*

---

### 閲覧メインのアプリ（EC 等）への組み込み

*Building this into browse-heavy apps (e-commerce and similar)*

**質問**（Anonymous）👍 1

> Apple Intelligenceはアクションがあるアプリは組み込み安そうに思いましたが、例えばECアプリなどの閲覧がメインのアプリにはどのように組み込むのがいいのでしょうか？機能を組み込んだ時に期待できるユーザー体験を教えていただきたいです

*Apple Intelligence seems easy to build into apps that have actions. How should we build it into apps whose main use is browsing, such as e-commerce apps? What user experience can we expect once the features are in?*

**回答**（Shun）

> セッションのなかでもご紹介させていただきましたが、ショッピングなどでは、ユーザーレビューなどをサマリーを生成して、簡潔なものを表示してあげるなど、情報の閲覧性の改善にご利用いただくとよいかと思います。

*As we showed in the session, for shopping and similar cases it works well to generate a summary of user reviews and show a concise version, so the information is easier to browse.*

---

### Core AI と Core ML の違い

*Difference between Core AI and Core ML*

**質問**（Anonymous）

> Core AI と以前からある Core ML はどのような違いがありますか？

*What is the difference between Core AI and the existing Core ML?*

**回答**（Shun）

> Core AIはニューラルネットワークを使ったモデルにおいて最適に動作するように作られており、また生成結果についても処理後ではなく、処理中からもAsyncで結果が受け取れます。Core MLについては、引き続きニューラルネットワーク以外のモデル（たとえば、decision trees or tabular feature engineering）などでは利用いただけるものとなってます。

*Core AI is built to run optimally for models that use neural networks, and you can receive generated results asynchronously while processing is still going, not only after it finishes. Core ML can still be used for models other than neural networks, for example decision trees or tabular feature engineering.*

**回答**（Shun）

> LLMであればほぼCore AIを前提に、その他既存の別なモデルについては、Core MLを使っていただくなど目的に応じて使い分けていただければ幸いです。

*For an LLM, assume Core AI almost entirely. For other existing models, please use Core ML according to the purpose.*

---

### Core AI / Core ML / MLX / Foundation Models の使い分け

*Choosing among Core AI, Core ML, MLX, and Foundation Models*

**質問**（Anonymous）

> Core AI / Core ML / MLX / Foundation Models をどう使い分けるのが良いのでしょうか？

*How should we choose among Core AI, Core ML, MLX, and Foundation Models?*

**回答**（Shun）

> Foundation Models については、オンデバイスで標準で入っている汎用的なモデルになっていますので、比較的ジェネラエルな生成結果に向いてます。もし何か特化した分析・推論を行いたい場合は、Core AI / MLX等をご利用ください。Core MLについては、従来のDecision Treeや回帰分析による予測など従来の統計手法を用いた推論は引き続きご利用いただけます。

*Foundation Models is a general-purpose model that comes standard on device, so it is relatively suited to general generation. If you want specialized analysis or inference, use Core AI, MLX, and so on. Core ML can still be used for inference with traditional statistical methods, such as decision trees and regression.*

**回答**（Shun）

> ただ、neural networksをベースとしたモデルの場合はCore AIが特化しているためパフォーマンス含めて良い結果となります。またCore AIの場合は推論途中にAsyncで生成結果を受け取れるのに対して、Core MLはバッチ処理完了後の結果生成となるため、結果表示をするという観点での機能が異なります。

*For models based on neural networks, Core AI is specialized for that and gives better results, including performance. With Core AI you can receive generated results asynchronously during inference, whereas Core ML produces results after batch processing completes, so the two differ in how you display results.*

**回答**（Shun）

> MLXについては既存のモデルをCore AIのようにコンバートするのではなく、モデル自体を自ら作りたい場合に適しているので、かなりアドバンスなユースケースに使われるとお考えください。

*MLX is suited to building the model yourself, rather than converting an existing model the way you would for Core AI. Think of it as being for quite advanced use cases.*

---

### オンデバイスモデルのトークン制限とコンテキスト管理

*Token limits and context management for the on-device model*

**質問**: スクショ上は本文非表示（回答内容からコンテキストウィンドウ・トークン制限に関する質問と推定）

*The question body is not visible in the screenshot. Inferred from the answer: it is about the context window and token limits.*

**回答**（Shun）

> 今の段階でオンデバイスモデルについては4096トークンでどのデバイスでも変更はありません。ただしモデル自体は機種によって異なってます。 なお、プロンプトをウィンドウサイズに納めるには、Instruments を使って利用状況を確認していただく他に、

*At this stage, on-device models are 4096 tokens on every device, with no change. The model itself differs by device. To fit a prompt into the window size, besides checking usage with Instruments,*

**回答**（Shun）

> iOS27から登場したDynamic Profileをご利用いただくと、全体としてのコンテキストはキープしつつも、モデルに渡すコンテキストを制限するなどの処理がしやすくなっています。

*Dynamic Profile, introduced in iOS 27, makes it easier to keep the overall context while limiting the context passed to the model.*

**回答**（Shun）

> ぜひ、下記のドキュメントなど（.historyTransformなど）を参照してみてください。
>
> https://developer.apple.com/documentation/foundationmodels/composing-dynamic-sessions-with-instructions-and-profiles

*Please see the documentation below, including `.historyTransform`: https://developer.apple.com/documentation/foundationmodels/composing-dynamic-sessions-with-instructions-and-profiles*

**回答**（Masashi / Apple）: 返信あり（スクショ上は本文非表示）

*There is a reply, but the body is not visible in the screenshot.*

---

### SystemLanguageModel のコンテキストサイズ（4096 トークン）

*Context size of SystemLanguageModel (4096 tokens)*

**質問**（Anonymous）👍 1

> iOS 27でもSystemLanguageModelのコンテキストサイズは4096のままでしょうか？

*Is the context size of SystemLanguageModel still 4096 on iOS 27?*

**回答**（Shun）

> オンデバイスのコンテキストウィンドウは4096トークンで変更はありません。

*The on-device context window is 4096 tokens, unchanged.*

---

### オンデバイス vs クラウドの使い分け指針

*Guidance on choosing on-device versus the cloud*

**質問**（Anonymous）👍 4

> オンデバイスモデルの考え方とても魅力的な一方でユーザー側の端末に負担を強いることになると考えています。端末の寿命も短くなると思いますが、Appleとしては、オンデバイスモデル中心で進めるべきかクラウドを積極的に利用すべきなのか指針があれば教えてください。

*The idea of on-device models is very attractive, but I think it places a burden on the user’s device, and that device lifespan will shorten. Does Apple have guidance on whether we should proceed centered on on-device models, or actively use the cloud?*

**回答**（Shun）

> iPhoneなどの電力消費という観点であれば、オンデバイスにとっては不利ではありますが、オンデバイスとPCCやサーバーサイドのLLMではできることの違いが大きいため、利用シーン次第で使い分けていただく、またオンデバイスでの実行の際は、不要な処理は行わず最小限にするなどの検討は必要かとは思います。

*From the standpoint of power consumption on iPhone and similar devices, on-device is at a disadvantage. What on-device can do differs a lot from PCC or a server-side LLM, so please choose based on the use case. When running on device, consider doing only the minimum and skipping unnecessary work.*

**回答**（Shun）

> ただし電力消費も極力は大きくならないようにOSとしては設計されており、また改善も進めております。もし気になるようでしたらInstrumentsなどをみながらアプリ内での処理の最適化をしていただくことをお勧めします。

*The OS is designed so power consumption does not grow more than necessary, and improvements are continuing. If you are concerned, we recommend optimizing processing in the app while looking at Instruments and similar tools.*

---

### Origami アプリの入手方法

*How to get the Origami app*

**質問**（Anonymous）👍 2

> OrigamiアプリはApp Storeからインストールできますか？日本のApp Storeで検索しても表示されません。

*Can the Origami app be installed from the App Store? It does not appear when I search the Japanese App Store.*

**回答**（Shun）

> https://developer.apple.com/documentation/FoundationModels/origami-crafting-a-dynamic-tutorial-for-apple-intelligence
>
> Origamiアプリはサンプルプロジェクトとして提供されておりますので、Xcode27 betaをダウンロードいただき、実機等で検証いただく必要があります。

*The Origami app is provided as a sample project, so you need to download the Xcode 27 beta and try it on a device. See https://developer.apple.com/documentation/FoundationModels/origami-crafting-a-dynamic-tutorial-for-apple-intelligence.*

---

### Siri の設計思想（Siri 完結 vs アプリ入り口）

*Design intent for Siri (finish in Siri, or use it as an entry to the app)*

**質問**（Anonymous）👍 2

> 思想として、全てのタスクがSiriだけで完結できるのがベストでしょうか。それとも、Siriはあくまで入り口であり、原則はアプリの画面を開く形がベストでしょうか。

*As a philosophy, is it best if every task can be completed with Siri alone? Or is Siri only an entry point, and is it best in principle to open the app’s screen?*

**回答**（Shun）

> 細かな操作はSiriからすべて行うことは難しいため、アプリの中でもっと頻繁に使われる機能から対応いただくのが良いかと思います。Siriでメインのところは操作した上で補う形でアプリを起動する形で導けますので、細かな設定が必要な部分はアプリのなかでというフローを検討いただくのが現実的かと思います。

*It is hard to do every fine-grained action from Siri, so it is better to support the features used more often inside the app first. You can have Siri handle the main parts and then launch the app to fill in the rest. A realistic flow is to keep parts that need detailed settings inside the app.*

---

## プラットフォーム / iOS 27

*Platform / iOS 27*

### iOS 27 SDK ビルド必須化のスケジュール

*Schedule for requiring builds with the iOS 27 SDK*

**質問**（Anonymous）👍 1

> 昨年iOS26SDKがアナウンスされた際、2026年4月以降はiOS26SDKでのビルドが必須となる、とありました。UISceneライフサイクルの必須化などに伴い、今回のiOS27SDKについても同様のことが検討されていますか？もしそうであれば、いつ頃を予定されていますか？ https://developer.apple.com/news/?id=6lxhtioi

*When the iOS 26 SDK was announced last year, it said builds with the iOS 26 SDK would be required from April 2026. With things like the UIScene lifecycle becoming required, is something similar being considered for the iOS 27 SDK? If so, about when? https://developer.apple.com/news/?id=6lxhtioi*

**回答**（Shun）

> 今の時点でXcode27でのアプリビルドの必須になる時期についてはアナウンスはありません。ご認識の通り、ここ数年、4月に切り替えをご案内していることが多いかとは思いますので、一つの目処としてお考えいただいてもいいかとは思います。ただし、状況によってタイミングが変わる可能性があることはご了承ください。

*There is no announcement yet of when building apps with Xcode 27 will become required. As you noted, in recent years the switch has often been announced in April, so you may treat that as one rough target. The timing may change depending on circumstances.*

---

### サイジング機能と既存の iPad リサイズの違い

*Difference between the new sizing feature and existing iPad resizing*

**質問**（Anonymous）👍 2

> 今回のサイジングの機能は、既存のiPad表示の自由にリサイズ出来る機能とは異なりますか？

*Is this sizing feature different from the existing ability to freely resize the iPad display?*

**回答**（Masashi / Apple）

> iPhoneアプリとしてビルドされたものが、iPadやMacのiPhoneミラーリングでリサイズできるというのが今回の新しい点になります。

*The new point is that something built as an iPhone app can be resized in iPhone mirroring on iPad and Mac.*

---

### UIKit でのリサイズ対応（SwiftUI 移行が難しい場合）

*Resize support in UIKit (when moving to SwiftUI is hard)*

**質問**（Anonymous）👍 2

> リサイズ対応について、UIKitで作られていてすぐにはSwiftUIには変更できない場合、どのように対処すると良いですか？

*For resize support, if the app is built with UIKit and cannot be changed to SwiftUI right away, how should we handle it?*

**回答**（Shun）

> フレームワークに関わらず、一番難しいのはコンテンツを固定のPixelで配置してしまっているケースかと思います。UIKitだとしても、Autolayoutをしっかりと活かしていただけると、リサイズにも十分に対応はできるかと思います。

*Regardless of framework, the hardest case is when content is laid out in fixed pixels. Even with UIKit, if you make good use of Auto Layout, you should be able to handle resizing well enough.*

---

### SwiftUI のレスポンシブレイアウト（列数の切り替え）

*Responsive layout in SwiftUI (switching the number of columns)*

**質問**（zunda）👍 1

> WWDC26で展開された「あらゆる画面サイズで完璧なレイアウトを実現しましょう」という観点でレイアウトを組む際に、画面横幅が狭い時は縦1列に並べ、広い時には2列、3列と表示しようとした際に、どのようなAPIを使うのが良いでしょうか？ViewThatFits, GeometryReader等だと辛い部分もありそうなため...

*From the WWDC26 angle of “let’s achieve a perfect layout at every screen size”: when a narrow width should show one vertical column and a wider width should show two or three columns, which API is good to use? ViewThatFits, GeometryReader, and similar options seem painful in places...*

**回答**（Masashi / Apple）

> Group Labでこのあたりが解説されているので是非ご覧ください！
>
> https://developer.apple.com/jp/videos/play/wwdc2026/8120/

*This is covered in a Group Lab. Please watch https://developer.apple.com/jp/videos/play/wwdc2026/8120/.*

---

### UIApplicationDelegate の一部移行（UISceneDelegate）

*Partial migration of UIApplicationDelegate (to UISceneDelegate)*

**質問**（Anonymous）👍 2

> UIApplicationDelegateは一部のみ使えなくなる認識でしたがあっていますか？

*I understood that only part of UIApplicationDelegate becomes unusable. Is that correct?*

**回答**（Shun）

> https://developer.apple.com/documentation/technotes/tn3187-migrating-to-the-uikit-scene-based-life-cycle
>
> こちらにもあります通り、4つのイベントにつきましては、UISceneDelegateへの移行をお願いしております。その他必要なものはそのままUIApplicationDelegateでご利用いただけます。

*As described in https://developer.apple.com/documentation/technotes/tn3187-migrating-to-the-uikit-scene-based-life-cycle, please migrate four events to UISceneDelegate. Anything else you need can still be used on UIApplicationDelegate.*

---

### iPhone のみ対応から iPad 対応へ（小規模チーム）

*From iPhone-only to iPad support (small teams)*

**質問**（Anonymous）👍 3

> 現状チームが小さくiPhoneのみの対応となっており、iPad対応などもしたいところです。ここら辺をいい感じに対応してくれる機能はないのでしょうか？

*Our team is small and we currently support iPhone only, and we would like to support iPad as well. Is there a feature that handles this nicely?*

**回答**（Masashi / Apple）

> すでにSwiftUIをご活用いただいているのであればいいポジションにいらっしゃるかと思います！ネイティブのコンポーネントを活用しながらフレキシブルなレイアウトを実現していくのが、基本的なアプローチになります。UIKitをお使いであれば、是非ともXcode 27で「このUIKitのコードベースをモダナイズして」といったようなプロンプトを使い、UIKitのModernization Skillを呼び出すことからスタートいただくとよろしいかと思います！

*If you are already using SwiftUI, you are in a good position. The basic approach is to use native components and build a flexible layout. If you use UIKit, a good start in Xcode 27 is a prompt such as “modernize this UIKit codebase,” which invokes the UIKit Modernization Skill.*

---

### Safari（iOS 27）の変更と Web 開発者向けポイント

*Safari changes in iOS 27, and what web developers should watch*

**質問**（Anonymous）👍 3

> iOS27からSafariにも変更が加えられるとお聞きしました。詳しい確定事項、webの開発者が気にするべきポイントがあればご教示ください

*I heard Safari will also change starting with iOS 27. If there are confirmed details, or points web developers should care about, please share them.*

**回答**（Shun）

> 私の方で細かい変更について把握できているわけではありませんが、互換性の向上や新機能の追加が多いという認識はしております。
>
> https://developer.apple.com/jp/videos/play/wwdc2026/204
>
> こちらのセッションで概要を、またそのセッションのなかで詳細は別なセッションでと案内されているかと思いますので、１つ目のセッションをご覧いただき、影響などがありそうか確認いただければと思ってます。

*I do not have a detailed grasp of the changes, but my understanding is that many of them are compatibility improvements and new features. The session at https://developer.apple.com/jp/videos/play/wwdc2026/204 covers the overview and, I believe, points to other sessions for details. Please watch that first session and check whether there is likely impact.*

---

### iOS 26 以降と iOS 18 以前のデザイン差への効率的な対応

*Handling design differences between iOS 26 and later and iOS 18 and earlier*

**質問**（Anonymous）👍 7

> iOS26以降とiOS18以前のアプリでデザインが違ってくると思いますが、開発する上で効率よくやる方法を知りたいです

*I think the design will differ between apps on iOS 26 and later and on iOS 18 and earlier. I want an efficient way to develop for that.*

**回答**（Masashi / Apple）

> まず、Xcode 27でビルドすることからスタートし、Liquid Glassをはじめとする新しいデザイン言語がどのような形でご自身のアプリに適用されるのかをご確認ください。そして、効率と効果の両面でおすすめなのが、ネイティブのコンポーネントをお試しいただくことです。そうすれば、iOS 18以前でも、iOS 26以降でも馴染み深いインタフェースを最小限のワークロードで実現できます。そして、もしご質問や、ご相談などございましたら、是非とも今後のイベントへのご参加もご検討ください。お会いできるのを楽しみにしてます！
>
> https://developer.apple.com/events/view/upcoming-events?languages=ja

*Start by building with Xcode 27, and check how the new design language, including Liquid Glass, is applied to your app. What we recommend for both efficiency and effect is to try native components. Then you can achieve a familiar interface on both iOS 18 and earlier and iOS 26 and later, with a minimal workload. If you have questions or want to talk it through, please also consider joining future events. We look forward to seeing you. https://developer.apple.com/events/view/upcoming-events?languages=ja*

---

## デザイン / Liquid Glass / Icon Composer

*Design / Liquid Glass / Icon Composer*

### Liquid Glass の強制適用と方向性

*Whether Liquid Glass becomes mandatory, and the direction*

**質問**（Anonymous）👍 10

> リキッドグラスは今後強制になると聞きましたが、方向性は変わらずでしょうか？

*I heard Liquid Glass will become mandatory. Is the direction unchanged?*

**回答**（Masashi / Apple）

> ネイティブコンポーネントの見た目が、Xcode 26/27でビルドしたアプリでは、Liquid Glassを活用したデザインになります。
>
> `UIDesignRequiresCompatibility`というフラグをお使いいただくことで、Xcode 26ではiOS 18以前のデザインを適用することができましたが、Xcode 27ではこのフラグは無効になります。
>
> 一方で、カスタムコンポーネントに関しましては、もちろんLiquid Glassをマテリアルとして設定することもできますが、今までと変わらない自由度がありますので自由な表現が可能です。
>
> もし何らかの理由でLiquid Glassのコンポーネントを使うべきでないと判断された場合は、カスタムコンポーネントの利用をご検討ください。

*In apps built with Xcode 26 or 27, native components take on a design that uses Liquid Glass. The `UIDesignRequiresCompatibility` flag let Xcode 26 apply the pre–iOS 18 design, but the flag is disabled in Xcode 27. Custom components can of course set Liquid Glass as a material, but they still have the same freedom as before, so you can express things freely. If for some reason you decide you should not use Liquid Glass components, consider custom components.*

---

### Liquid Glass 適用の必須化時期（2027年春）

*When applying Liquid Glass becomes required (spring 2027)*

**質問**（Anonymous）👍 2

> リキッドグラスのデザイン適用は2027年の春頃に必須になるのでしょうか？現状はリキッドグラスのデザイン適用をオフにする設定がxcodeに用意されていましたが、暫定的なものだと理解しています。

*Will applying the Liquid Glass design become required around spring 2027? Xcode currently has a setting to turn that design off, and I understand it is provisional.*

**回答**（Masashi / Apple）

> UIDesignRequiresCompatibilityというフラグがXcode 26ではお使いいただけておりましたが、Xcode 27ではそれが無効となります。Xcode 27でネイティブコンポーネントをお使いいただく場合は、Liquid Glassのデザインが反映されます。

*The `UIDesignRequiresCompatibility` flag was available in Xcode 26, but it is disabled in Xcode 27. If you use native components in Xcode 27, the Liquid Glass design is applied.*

---

### `tabAccessoryView` の使い方

*How to use `tabAccessoryView`*

**質問**（Anonymous）👍 2

> Liquid GlassのtabAccessoryViewはHIGでも説明ないので何者なのかが分からないのですが、あれどうやって使ったら良いんですか？（どう使われることを期待していますか？） (edited)

*Liquid Glass’s `tabAccessoryView` is not explained in the HIG, so I don’t know what it is. How should we use it? (How do you expect it to be used?) (edited)*

**回答**（Masashi / Apple）

> ドキュメントではなくビデオで解説しておりますので、是非ご確認いただければと思います！
>
> https://www.youtube.com/watch?v=DS2ildqCrB0

*It is explained in a video rather than in documentation. Please watch https://www.youtube.com/watch?v=DS2ildqCrB0.*

---

### 検索タブバーの振る舞い（UI Layer）

*Behavior of the search tab bar (UI layer)*

**質問**（Anonymous）👍 7

> UI Layerにおける検索タブバーの振る舞いが、iOS 26のApple製アプリでもそれぞれ異なっており（またマイナーアップデートごとに更新されており）、どう実装するのがベストプラクティスなのかわかりません。HIGもWWDCで更新されましたがうまいこと理解ができず、わかりやすく解説いただけると助かります。

*The behavior of the search tab bar in the UI layer differs across Apple’s own apps on iOS 26, and it is updated with each minor release, so I don’t know the best practice for implementation. The HIG was also updated at WWDC, but I couldn’t quite follow it. A clear explanation would help.*

**回答**（Masashi / Apple）

> ぜひ私どもの1 on 1アポイントメントや、ワークショップへのご参加をご検討ください！じっくり解説させていただきます！！
>
> https://developer.apple.com/events/view/upcoming-events?languages=ja

*Please consider joining our 1-on-1 appointments or workshops. We will explain it carefully. https://developer.apple.com/events/view/upcoming-events?languages=ja*

---

### Liquid Glass 設定値の API（Safari / WKWebView）

*API for Liquid Glass settings (Safari / WKWebView)*

**質問**（Anonymous）

> LiquidGlassのultra clearやfull tint等、ユーザーが設定した値を受け取るAPIはありますか？SafariやWKWebViewで利用できるLiquidGlass APIは提供されるでしょうか。

*Is there an API that receives the values the user set for Liquid Glass, such as ultra clear or full tint? Will a Liquid Glass API usable in Safari or WKWebView be provided?*

**回答**（Masashi / Apple）

> いいえ。Liquid Glassの見え方によってコンテンツレイヤーの表示を変えるような挙動は想定しておりません。SafariやWKWebViewで表示するのは、Webページになりますので、コンテンツレイヤに表示するものとお考えいただくとよろしいかと思います！

*No. We do not expect behavior that changes how the content layer is displayed based on how Liquid Glass looks. What Safari and WKWebView display is a web page, so please think of it as something shown in the content layer.*

---

### Liquid Glass の個人設定とデザイン基準

*Personal Liquid Glass settings, and what to design against*

**質問**（Anonymous）👍 13

> リキッドグラスのかかり具合を個人設定できるようになると、リキッドグラスのデザインはどれを基準にして行うのがいいでしょうか？

*If people can personally set how strongly Liquid Glass is applied, which Liquid Glass look should we use as the baseline for design?*

**回答**（Masashi / Apple）

> Liquid Glassの特定の見え方を基準としてデザインしない方が良いですね。Liquid Glassによって構成されるUIレイヤは画面全体を覆うことはなく、あくまでナビゲーションとアクションを提供する一部でしかありません。ですので、大部分を占めるコンテンツレイヤでブランドを表現することを考えていただけるとよろしいかと思います！

*It is better not to design against one specific look of Liquid Glass. The UI layer made of Liquid Glass does not cover the whole screen. It is only a part that provides navigation and actions. So think about expressing the brand in the content layer, which occupies most of the screen.*

---

### Icon Composer 2 と OS 世代ごとの見え方

*Icon Composer 2 and how icons look on each OS generation*

**質問**（Anonymous）

> IconComposer2で作成したアイコンは、iOS18やiOS26でも同じような外観にみえるのでしょうか？OS世代ごとに見栄えの確認が必要でしょうか？

*Do icons created with Icon Composer 2 look similar on iOS 18 and iOS 26 as well? Do we need to check the appearance for each OS generation?*

**回答**（Masashi / Apple）

> Icon ComposerにiOS 26と27での見え方を切り替えられるスイッチが付いてます！そちらをご活用ください。 なおiOS 18にはiOS 26の時点で後方互換性がありましたのでそれをそのままご活用いただけるとお考えください。

*Icon Composer has a switch that toggles the look on iOS 26 and iOS 27. Please use that. iOS 18 already had backward compatibility as of iOS 26, so you can keep using that.*

---

### ポート時の帯デザイン（過去 WWDC セッション）

*The band design for portrait (a past WWDC session)*

**質問**（Anonymous）

> ポート時の帯デザインの発表がされていた過去のWWDCの発表(セッション)をもう一回教えてください

*Please tell me again which past WWDC session announced the band design for portrait. “ポート” is read here as short for portrait (ポートレート). That reading is not confirmed against the session.*

**回答**（Masashi / Apple）

> こちらです！ぜひご覧ください！
>
> https://developer.apple.com/jp/videos/play/wwdc2024/10085/

*This one. Please watch https://developer.apple.com/jp/videos/play/wwdc2024/10085/.*

---

## 開発ツール / Xcode

*Developer tools / Xcode*

### Xcode Agent の性能・立ち位置

*Capability and standing of Xcode Agent*

**質問**（Anonymous）

> xcode agentの性能は今どんな立ち位置にいると認識しておりますか？また、得意不得意、他手段と比較したメリットデメリットあれば知りたいです

*How do you see the current standing of Xcode Agent’s capability? I also want strengths and weaknesses, and pros and cons compared with other approaches.*

**回答**（Shun）

> Apple Platform の開発については、Xcodeに独自のSkillが入っており、またシミュレーターやInstrument計測結果をもとにしたパフォーマンス改善など専門特化した機能が増えていますので、使いやすさは向上していると考えております。ぜひまだ不十分なところ使いづらいところがありましたら、 http://feedbackassistant.apple.com/ へご登録いただけますと幸いです。

*For Apple platform development, Xcode includes its own Skills, and specialized features are increasing, such as performance improvements based on the simulator and Instruments measurements, so we think it is becoming easier to use. If something is still insufficient or hard to use, please submit it at http://feedbackassistant.apple.com/.*

---

### Xcode コーディングエージェントの外部モデルとデータ送信先

*External models for the Xcode coding agent, and where data is sent*

**質問**（Anonymous）👍 1

> Xcodeのコーディングエージェントが外部モデルを使う場合、ソースコード、コメント、ビルドログ、クラッシュログ、プロンプト履歴といったデータはどこに送信されますか？

*When Xcode’s coding agent uses an external model, where are data such as source code, comments, build logs, crash logs, and prompt history sent?*

**回答**（Shun）

> それぞれの外部モデルのプロバイダーさんに必要なものは送信されます。Appleに送信されるものはない認識です。なお、外部への送信が懸念される場合は、LM Studioなどを利用してローカルモデルを使って動作させることを検討してみてください。

*What each external model provider needs is sent to that provider. My understanding is that nothing is sent to Apple. If sending data externally is a concern, consider running a local model with LM Studio or similar.*

---

### Xcode のチーム活用（PM・デザイナー・開発者）

*Using Xcode as a team (PMs, designers, and developers)*

**質問**（Anonymous）👍 1

> Xcodeをチームで活用する方法をより詳細に知りたいです。PM、デザイナー、開発者で知見のある領域が異なりますが、そのギャップを活かしてより良いアイデアを得るための良い活用方法がわかるようなビデオや記事はありませんか？

*I want more detail on how to use Xcode as a team. PMs, designers, and developers know different things. Are there videos or articles that show a good way to use that gap to get better ideas?*

**回答**（Shun）

> 是非見ていただきたいものとして、 https://developer.apple.com/jp/videos/play/wwdc2026/227 というセッションがあります。 PMさんやデザイナーさんがいろいろプロンプトを利用してプロトタイプを作ってみることにより、実際の動作含めて実現できること、できないこと、よりアプリをいい体験にするアイデアなどを試すことができます。具体的に動かして試せるというのが大きいため、開発者の方とのコミュニケーションがスムーズになるかと思います。

*One session to watch is https://developer.apple.com/jp/videos/play/wwdc2026/227. When PMs and designers use prompts to build prototypes, they can try what can and cannot actually be done, including real behavior, and try ideas for a better app experience. Being able to run it and try it concretely is a big deal, so communication with developers should become smoother.*

---

### Xcode Intelligence と Siri（ChatGPT / Claude 未選択時）

*Xcode Intelligence and Siri (when ChatGPT or Claude is not selected)*

**質問**（Anonymous）

> Xcodeでインテリジェンスで質問するときにChatGPTやClaudeの選択があったが選択をしなければSiriが回答をしてくれるのか？

*When asking a question with Intelligence in Xcode, there was a choice of ChatGPT or Claude. If I don’t select one, does Siri answer?*

**回答**（Shun）

> Siriはデバイスを利用されている一般のユーザーさんからの依頼や質問に答えるのがメインとなっておりまして、Xcode上で開発に関すること、Siriが答えるという機能はありません。従来どおりChatGPTやClaude等は引き続きご利用いただけます。

*Siri’s main role is answering requests and questions from general users of the device. There is no feature where Siri answers development questions inside Xcode. You can continue to use ChatGPT, Claude, and so on as before.*

---

### Xcode 27 と Xcode 26 のエージェント機能の差異

*Differences in agent features between Xcode 27 and Xcode 26*

**質問**（Anonymous）👍 1

> Xcode 27とXcode26のエージェント機能の差異について教えてください。同じLLMを使う限りは出力に大きな差異はないでしょうか？それともXcode27を使った方が良い回答が得られるのでしょうか？

*Please tell me the differences in agent features between Xcode 27 and Xcode 26. As long as we use the same LLM, is there no large difference in output? Or do we get better answers by using Xcode 27?*

**回答**（Shun）

> Xcode27内でSkill自体が改良されていたり、Xcode内のMCPの機能が充実していることから、Xcode26の中で行えることよりも精度や実行範囲が異なっています。Xcode27を使っていただいた方がより広域なことができますので、是非一度お試ください。

*Skills themselves have been improved inside Xcode 27, and MCP features inside Xcode are richer, so accuracy and the range of what can be executed differ from what you can do in Xcode 26. You can do a wider range of things with Xcode 27, so please try it.*

---

### Xcode エージェントのローカル実行とチップ性能差

*Running the Xcode agent locally, and performance differences by chip*

**質問**（Anonymous）👍 2

> Xcodeのエージェントはローカル完結で動かすことができますか？またチップ（M5 Pro or Maxなど）による性能差はありますか？

*Can Xcode’s agent run entirely locally? Are there performance differences by chip, such as M5 Pro or Max?*

**回答**（Shun）

> Ollama, LM Studioなどをローカルで起動いただき、そこでモデルを動作させることでXcodeから接続して動作させることができます。
>
> https://developer.apple.com/jp/videos/play/wwdc2026/232?time=693
>
> MLXを使ってローカルモデルでXcodeを使うデモもありますのでよかったらご覧ください。チップだけではなくメモリーサイズや選択されるモデルそのものによっても性能差はでてきます。

*If you start Ollama, LM Studio, and so on locally and run a model there, you can connect from Xcode and run it. There is also a demo of using Xcode with a local model via MLX: https://developer.apple.com/jp/videos/play/wwdc2026/232?time=693. Performance differences come not only from the chip but also from memory size and the model you choose.*

---

### Xcode 26 の最低保証 OS

*Minimum OS supported by Xcode 26*

**質問**（Anonymous）👍 3

> Xcode26の最低保証OSはiOS15でしょうか？去年はiOS13と書かれていましたが、途中からiOS15との記載に変わりました。実際iOS12ターゲットでビルドしても現在も承認されます。

*Is the minimum supported OS for Xcode 26 iOS 15? Last year it said iOS 13, then the description changed to iOS 15 partway through. In practice, builds that target iOS 12 are still approved.*

**回答**（Shun）

> https://developer.apple.com/jp/support/xcode/ こちらのページをご確認ください。シミュレーターや実機検証が古いバージョンだとサポートされていかなくなっております。ただし、ビルドターゲットとしては現在のところiOS12まで受け付けておりますが、セキュリティの観点等も踏まえた上で徐々に上がっていくことが想定されますので、できる限り対応OSについては新しいOSがでましたら上げていくご検討対応をいただければと思っております。

*Please check https://developer.apple.com/jp/support/xcode/. Simulator and device testing are no longer supported for older versions. As a build target, iOS 12 is still accepted for now, but it is expected to rise gradually, including for security reasons. Please consider raising the supported OS as much as you can when a new OS comes out.*

---

### SwiftUI を Xcode 以外の IDE で開発・プレビュー

*Developing and previewing SwiftUI in an IDE other than Xcode*

**質問**（Anonymous）

> SwiftUI(特に Liquid Glass など最新UI)の開発・プレビューを、Xcode以外のIDE(VSCode等)でも完結できるようにする計画はありますか。現状はXcode必須で、AIエージェント中心の開発フローと相性が悪いと感じています。

*Are there plans to make development and preview of SwiftUI, especially the latest UI such as Liquid Glass, possible entirely in an IDE other than Xcode, such as VS Code? Right now Xcode is required, and I feel that does not fit a development flow centered on AI agents.*

**回答**（Shun）

> xcrun agent skills export とコマンド叩いていただけますと、Xcode27に内包されている各 Skill が書き出せますのでそちらを、他の環境へ移植いただければ、Xcode内でのできることと同じような形になります。また、XcodeのMCPよりシミュレーターの操作もできるようになっておりますので、CLIなどのLLMを使っていただければ、なんらか連携できるのではないかと思いますが、

*If you run `xcrun agent skills export`, you can export each Skill included in Xcode 27. If you port those to another environment, it becomes similar to what you can do inside Xcode. You can also operate the simulator through Xcode’s MCP, so if you use an LLM from the CLI, some integration may be possible, but*

**回答**（Shun）

> 私がVSCodeなどの環境を理解できておらずすみません。また、上記でも実現ができないようでしたら、 http://feedbackassistant.apple.com/ へ、ご希望の連携機能などをユースケースとあわせてご記入いただけますと幸いです。Xcode自体もまた今後も進化していきますので、そも（スクショ上は本文途切れ）

*I’m sorry I don’t understand environments such as VS Code. If the above still cannot do what you want, please describe the integration you want, along with the use case, at http://feedbackassistant.apple.com/. Xcode itself will keep evolving, so (the body is cut off in the screenshot).*

---

### Xcode 27 のデフォルト Skill の個別オン・オフ

*Turning Xcode 27’s default Skills on and off individually*

**質問**（Anonymous）

> Xcode27でエージェンティック開発する場合、XcodeのデフォルトSKILLが多数ありますが、個別にオン・オフはできますか？

*When doing agentic development in Xcode 27, there are many default Xcode Skills. Can they be turned on and off individually?*

**回答**（Shun）

> 今の段階で個別にOn/off機能は提供されておりませんが、それぞれのAgentに対してのインストラクション・追加のSkillを入れることなどはできます。下記のドキュメントをご確認ください
>
> https://developer.apple.com/documentation/xcode/extending-and-customizing-agents

*At this stage there is no feature to turn them on and off individually, but you can add instructions and extra Skills for each agent. See https://developer.apple.com/documentation/xcode/extending-and-customizing-agents.*

---

### エージェント作成デザインの Figma 書き出し

*Exporting an agent-created design to Figma*

**質問**（Anonymous）👍 4

> エージェントが作成したデザインをFigmaに書き出すスキルはありますか？

*Is there a skill that exports a design created by the agent to Figma?*

**回答**（Masashi / Apple）

> Xcode → Figmaという方向ですと現時点ではオフィシャルな方法はない認識です。 Figma → Xcodeであれば、この度アナウンスされたプラグインをご活用いただけます。
>
> https://help.figma.com/hc/en-us/articles/41061095668759-Xcode-and-Figma-Set-up-the-MCP-server

*In the Xcode-to-Figma direction, I don’t believe there is an official method at this time. For Figma to Xcode, you can use the plugin that was announced: https://help.figma.com/hc/en-us/articles/41061095668759-Xcode-and-Figma-Set-up-the-MCP-server.*

---

## App Store

### App Intents 搭載アプリのストア申請（機能説明・デモ動画）

*Submitting an app that includes App Intents (feature description and demo video)*

**質問**（Anonymous）👍 1

> AppIntentsを内包したアプリをストア申請する際、どの程度まで機能の説明をするべきでしょうか？たとえばデモビデオなどでSiriとの連携の補足説明を追加した方がよいでしょうか？

*When submitting an app that includes App Intents, how much of the functionality should we explain? For example, should a demo video add a supplementary explanation of the Siri integration?*

**回答**（Shun）

> アプリ内にある同じ機能でしたら特に明記していただかなくても良いかとは思いますが、不安な場合は、App Review 1on1アポイントメントにてご確認いただけると確実かと思います。
>
> https://developer.apple.com/events/view/upcoming-events?search=App%20Reviewのアポイントメント&topics=app-store-distribution-marketing

*If it is the same feature that already exists inside the app, I don’t think you especially need to state it. If you are unsure, checking at an App Review 1-on-1 appointment is the sure way. https://developer.apple.com/events/view/upcoming-events?search=App%20Reviewのアポイントメント&topics=app-store-distribution-marketing*

---

### 検索表示用の画像アセット（スクリーンショット流用）

*Image assets for search results (reusing screenshots)*

**質問**（Anonymous）👍 2

> 新しく設定できるようになる画像アセットは検索時の表示にも使われているという話でしたが、ここは既存のスクリーンショットを表示させることも可能でしょうか？（1枚の大きな画像で表示された方がいいか、3枚のスクリーンショットが並ぶ方か、どちらが効果が高いか不明のため効果検証はしたい）

*I heard the newly configurable image assets are also used in search results. Can existing screenshots be shown there? I don’t know whether one large image or three screenshots side by side is more effective, so I want to test it.*

**回答**（Anonymous）

> 現時点ではApp Store Connect上でAsset Libraryから画像をどのように設定いただけるかは情報が公表されていないため、今後のアップデートを是非楽しみにお待ちいただければと思います。

*At this time, information has not been published on how to set images from the Asset Library in App Store Connect, so please look forward to a future update.*

---

## 運営・その他

*Logistics and other*

### 時間内に取り上げられなかった質問

*Questions that were not taken up in time*

**質問**（Anonymous）👍 10

> 時間内に取り上げられなかった質問は後日回答いただけるのでしょうか？

*Will questions that were not taken up within the time be answered later?*

**回答**: 1件の返信あり（スクショ上は本文非表示）

*There is one reply, but the body is not visible in the screenshot.*

---

### 「毎日使いたくなるアプリ」の共通点

*What “apps people want to use every day” have in common*

**質問**（Anonymous）👍 4

> Appleは『毎日使いたくなるアプリ』には、どんな共通点があると考えていますか？

*What common traits does Apple think “apps people want to use every day” have?*

**回答**: 未回答（スクショ上は返信なし）

*Unanswered. No reply is visible in the screenshot.*

---

### AI 時代におけるアプリの役割

*The role of apps in the AI era*

**質問**（Anonymous）👍 4

> AIが何でもできる時代に、Appleはアプリという存在が今後どんな役割を持つと考えていますか？

*In an era when AI can do anything, what role does Apple think apps will have going forward?*

**回答**: 未回答（スクショ上は返信なし）

*Unanswered. No reply is visible in the screenshot.*
