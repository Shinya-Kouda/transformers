<!---
Copyright 2020 The HuggingFace Team. All rights reserved.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->

# How To Request Support

これはオープンソースプロジェクトですので、他のプロジェクトと同様に、すべてのヘルプ要請に答える義務はないことをご了承ください。

しかし、私たちは、必要だと思われるときにはいつでも助けを求めていただきたいと思っています。なぜなら、お客様のニーズや誤解をより深く理解することができ、さらには、このライブラリーをより良くするためにお客様にご協力いただけるからです。とはいえ、このドキュメントの主な目的は、理解されサポートを受ける機会を増やすために、どのようにリクエストを作成すればよいかのガイドラインを提供することです。

サポートを受けるためには、主に2つの場所があります: [the forums](https://discuss.huggingface.co/) と [the GitHub issues](https://github.com/huggingface/transformers/issues)です。

## The Forums

[The user forums](https://discuss.huggingface.co/) はライブラリーユーザーの幅広いコミュニティに支えられ、必要に応じて開発者がバックアップします。

このライブラリの導入で困ったことや質問がある場合、あるいは新機能について議論したい場合は、まずフォーラムでの議論をご検討ください。テーマが明確になり、それでもライブラリ開発者のサポートが必要だと感じた場合にのみ、[issue](https://github.com/huggingface/transformers/issues)の提出に進んでください。

特に、「説明してください」という質問や、客観的に見て非常にユーザーに特化した機能の要望は、すべてフォーラムに属します。以下はそのような質問の例です。

* "カスタマーサポートサービス用のRL-Agent内でBertModelを使用したいと思います。ChatBotModelでBertForMaskedLMを使うにはどうしたらいいですか？"

* "T5がT5Modelの下に位置埋め込み行列を持たない理由を説明してもらえますか？"

* "翻訳の生成パラメータはどのように設定すればいいですか？"

* "De->Enの翻訳でT5をトレーニングするには？"


## The GitHub Issues

バグを示唆するものは、すべて[issues](https://github.com/huggingface/transformers/issues)としてオープンにすべきです。

課題を作成する前に、以下のガイドラインを読む必要はありません。しかし、もしあなたの課題に返信がないことに気づいたら、開発者がその品質に1つまたはいくつかの問題を抱えている可能性があります。そのような場合は、以下の項目を読んで、課題の内容を調整するとよいでしょう。

1. 問題を投稿する前に、まず既に投稿された問題を検索してみてください。

    もしGoogleを使っているなら以下のように検索してください。

    ```
    "huggingface" "transformers" your query
    ```

    最初の2つの単語を引用することで、Googleは検索を「huggingface transformers」の文脈に限定することができます。残りの部分はあなたのクエリで、一般的にはソフトウェアが失敗したときのエラーメッセージになります。詳細については後ほど説明します。

    このようなクエリの結果は、通常、GitHub issues、Hugging Face Forum、StackExchange、およびブログに一致します。

    関連するヒントが見つかった場合、さらに質問がある場合は、そこで議論を続けることもできます。

    もし見つけたものが似ていても問題の答えにならない場合は、新しいissueを投稿し、見つけた類似のissuesやフォーラムでの議論へのリンクを添付してください。

    いくつかの例を見てみましょう。

    エラーメッセージは、しばしばアサーションと呼ばれ、何が悪かったのかを教えてくれます。以下にアサーションの例を示します:

   ```python
   Traceback (most recent call last):
     File "<string>", line 1, in <module>
     File "/transformers/src/transformers/__init__.py", line 34, in <module>
       from . import dependency_versions_check
     File "/transformers/src/transformers/dependency_versions_check.py", line 34, in <module>
       from .file_utils import is_tokenizers_available
     File "/transformers/src/transformers/file_utils.py", line 40, in <module>
       from tqdm.auto import tqdm
    ModuleNotFoundError: No module named 'tqdm.auto'
    ```

   これにより、プログラムが失敗する前に行われた呼び出しの全スタックを見ることができます。これにより、プログラムがなぜ失敗したのかを知ることができます。

   上の例に戻ります。このエラー検索を受けた場合、エラーの一番最後の行を見てみましょう:

   ```python
    ModuleNotFoundError: No module named 'tqdm.auto'
    ```

    そして今度はそれを使って、お気に入りの検索エンジンで検索を行うことができます:

    1. first for `"huggingface" "transformers" "ModuleNotFoundError: No module named 'tqdm.auto'"`
    2. if you don't find relevant results, then search for just `"ModuleNotFoundError: No module named 'tqdm.auto'"`
    3. and finally if nothing still comes up, then remove the outside quotes: `ModuleNotFoundError: No module named 'tqdm.auto'`

   エラーの中にお客様のファイルシステムに固有のビットを含むメッセージが含まれている場合、他のユーザーがお客様のファイルシステムと同じものを持っているとは限らないため、検索クエリでは必ずそれらを削除してください。例えば、以下のようになります:

   ```bash
   python -c 'open("/tmp/wrong_path.txt", "r")'
   Traceback (most recent call last):
     File "<string>", line 1, in <module>
   FileNotFoundError: [Errno 2] No such file or directory: '/tmp/wrong_path.txt'
   ```
   このとき検索すべきクエリは以下です: `"FileNotFoundError: [Errno 2] No such file or directory"`

   削除したローカル情報がエラーメッセージの中にあって、それを削除した場合、クエリが正確でなくなるので、二重引用符を削除する必要があるかもしれません。つまり、エラーメッセージが次のようなものだった場合:

   ```bash
      ValueError: '/tmp/wrong_path.txt' cannot be found
   ```

   このとき検索すべきクエリは `"ValueError" "cannot be found"` です。

   検索してみると、引用符をあまり使わない場合、検索エンジンは様々な関連性のない検索結果を返してくることに気づくでしょう。

   いろいろな方法を試して、最も満足のいく結果が得られる方法を見つけてください。

2. 問題を簡潔にまとめ、開発者があなたの状況を理解するのに役立つと思われる情報を提供してください。あなたのコードを見たことがない人、あなたのカスタムセットアップについて何も知らない人の立場になって考えてみてください。これは、何を共有すべきか、何を共有すべきでないかを直感的に理解するのに役立ちます。

3. ソフトウェアのエラーが発生した場合は、常にすべてのtracebackを提供してください。例えば:

   ```python
   $ python -c 'import transformers'
   Traceback (most recent call last):
     File "<string>", line 1, in <module>
     File "/transformers/src/transformers/__init__.py", line 34, in <module>
       from . import dependency_versions_check
     File "/transformers/src/transformers/dependency_versions_check.py", line 34, in <module>
       from .file_utils import is_tokenizers_available
     File "/transformers/src/transformers/file_utils.py", line 40, in <module>
       from tqdm.auto import tqdm
   ModuleNotFoundError: No module named 'tqdm.auto'
   ```

   これと比較し、エラーメッセージの最後の行だけを提供する場合は不十分です:
   ```python
   ModuleNotFoundError: No module named 'tqdm.auto'
   ```
   

   アプリケーションが複数のGPU上で動作していて（例：`DistributedDataParallel`の下で）、通常、すべてのログやトレースバックが複数回出力される場合は、そのコピーを1つだけ貼り付けるようにしてください。並列プロセスからのトレースバックが混在することがあるので、これらを分離するか、ロガーを変更して `local_rank==0` のときだけログを取るようにして、1つのプロセスだけがログを取るようにしてください。

4. トレースバック、コマンドライン命令、あらゆるタイプのコードを引用する際には、必ずエディタウィンドウ内で3重のバックスティックで囲んでください:

   ````
   ```
   git clone https://github.com/huggingface/transformers
   cd transformers
   pip install .
   ```
   ````

   長い引数リストを持つコマンドラインの場合は、バックスラッシュや改行を使って分解することをご検討ください。以下は、良いコマンドラインの引用の例です:

   ```bash
    cd examples/seq2seq
    python -m torch.distributed.launch --nproc_per_node=2 ./finetune_trainer.py \
    --model_name_or_path sshleifer/distill-mbart-en-ro-12-4 --data_dir wmt_en_ro \
    --output_dir output_dir --overwrite_output_dir \
    --do_train --n_train 500 --num_train_epochs 1 \
    --per_device_train_batch_size 1  --freeze_embeds \
    --src_lang en_XX --tgt_lang ro_RO --task translation \
    --fp16 --sharded_ddp
   ```

   分割しないと、水平方向にスクロールしなければならず、何が起きているのかをすぐに確認するのは非常に困難です。

   バックスラッシュを使うことで、コマンドを編集することなく、直接コンソールにコピーして実行することができます。

5. 開発者が問題を素早く特定するのに役立つと思われる重要な情報だけを記載してください。

   例えば、アプリケーションは膨大な量のログを作成することがよくあります。ログの全部または一部を提供することが有用かどうかを自問してください。

   100～1000行のログを問題に貼り付けることは、ログの適切な部分がどこにあるかを把握するのに多くの時間を要するため、すぐに嫌がられます。

   完全なログを添付する場合は、コメントエディタのウィンドウで以下のようなhtmlコードで囲んで行うと便利です:

   ```
   <details>
   <summary>Full log</summary>
   <pre>

   many
   lines
   go
   here

   </pre>
   </details>
   ```

   これは、必要に応じて開くことができますが、それ以外はほとんどスペースをとりません。

   <details>
   <summary>Full log</summary>
   <pre>
   many
   lines
   go
   here
   </pre>
   </details>

    pastebinサービスへのリンクを提供することもできますが、これはあまり有益ではありません。なぜなら、これらのリンクはすぐに期限切れになる傾向があり、あなたの問題の将来の読者は、そのログファイルにもうアクセスすることができず、いくつかの文脈が欠けてしまうかもしれないからです。

6. もしあなたのコードに問題があるなら、そのコードを最小限の例に減らして、それでも問題を示すようにしてください。その方法がわからない場合は、フォーラムでお尋ねください。私たちには、あなたのカスタムコードをすべて理解するための時間的余裕はありませんので、ご了承ください。

   もしあなたが本当に短い再現可能なコードを作ろうとしたが理解できなかった場合、トレースバックがあれば開発者は何が起こっているかを知るのに十分な情報を得ることができるかもしれません。しかし、それだけでは不十分で、再現できなければ、本当の意味での解決にはなりません。

   最初から問題が解決できなくても落胆しないで、できる限りのことを教えてください。

   セットアップにカスタムデータセットが含まれている場合、問題を再現するための最良の方法は、問題を示す[Google Colab notebook](https://colab.research.google.com/)を作成し、問題がまだ存在することを確認したら、そのノートブックへのリンクをIssueに含めることです。ただし、開いているノートブックのロケーションバーのURLをコピー＆ペーストしないようにしてください。代わりに、ノートブックの右上隅にある「Share」をクリックし、「Get Link」を選択して、表示されたパブリックリンクをコピー＆ペーストしてください。

7. もしあなたがこのプロジェクトのコードやサンプルアプリケーションをフォークオフしたならば、どうか私たちにあなたのコードリポジトリを調べてあなたが何をしたかを把握するように頼まないでください。コードはすでに非常に複雑で、差分を取る簡単な方法がなく、それが小さな差分でない限り、長い調査をする時間のある人を見つけることはできないでしょう。とはいえ、フォーラムでは気前よくやってくれる人がいるかもしれません。

8. 問題を報告する前に、まず、あなたの環境をこのライブラリの最新の公式バージョンにアップデートしてみてください。私たちには、古いバージョンをデバッグするリソースがありませんので、最新のリリースバージョンで修正されたバグがある可能性があります。

   特にAPIが変更された場合には、お使いの環境でサポートされている最も高いバージョンのライブラリに対して問題を提起することになります。

   もちろん、ライブラリをアップグレードした場合は、問題が残っているかどうかを必ず再テストしてください。

9. あなたのカスタムデータを使って問題を再現してほしいという依頼はご遠慮ください。そのため、HF datasetsでサポートされている既存のデータセットを使用するか、オンザフライで小さなサンプルを生成するコードを提供していただくか、その他の迅速かつ簡単な方法で入手していただく必要があります。

   使用するのにライセンスや許可を必要とするような、パブリックドメインでないデータは送らないでください。

10. 複数の開発者をタグ付けすることが想定されていることがわかっている場合を除き、そのissueで複数の開発者をタグ付けしてはいけません。これは、あなたが開発者に尋ねてタグ付けすることを明示的に許可された場合や、issueテンプレートでそうするよう指示されている場合に限ります。

   issueテンプレートの「どのドメインに誰をタグ付けするか」という部分は、ユーザーが質問を、プロジェクトの特定のドメインのメンテナとして指定されている適切な開発者に向けるためのものです。開発者は、問題を前進させるのに役立つと思えば、自分の判断で他の開発者をタグ付けすることができます。

   現在、私たちはトリアージサービスを提供していませんが、あなたの能力を信頼して、適切なドメインを特定し、問題にタグ付けする人を決定してください。もしわからない場合は、フォーラムを利用してアドバイスを求めてください。

   疑問がある場合は、特定の人物をタグ付けしないようにしてください。文脈や許可を得ずに複数の人をタグ付けした場合、何の反応も得られなくても驚かないでください。誰かをタグ付けするたびに、その人は通知を受け取り、あなたはその人の時間を勝手に使っていることを忘れないでください。その点をご理解ください。

   過去に開発者に助けてもらったことがあっても、その開発者を今後のissueにタグ付けしないでください。ただし、質問しているドメインのissueテンプレートにその開発者が記載されている場合や、その開発者が今後のissueにタグ付けすることを明確に許可した場合は除きます。

   特定の開発者がプロジェクトの特定の領域で複数回のコミットや最近のコミットを行っているのを見て、それがあなたのissueに関連していると感じたとしても、その開発者をタグ付けするのは良い理由ではありません。様々な開発者が前進を妨げるものを修正しているかもしれませんが、多くの場合、彼らの作業は全く異なる領域に焦点を当てています。そして、彼らは目の前の問題であなたを助ける方法を知っているかもしれませんし、知らないかもしれませんが、彼らが独自の専門性を持つドメインに焦点を当てた方が、コミュニティ全体にとってはるかに有益なのです。

11. 編集ボタンを使います。時間をかけて、再読し、言葉遣いや書式を改善して、できるだけわかりやすい投稿やコメントにしてください。

    複数のコメントを連続して投稿することは避けてください。各コメントは、その課題にタグ付けされた開発者への通知を発生させます。たまたま複数のコメントを連続して投稿し、まだ誰もフォローアップしていない場合は、それらのコメントを1つまたはいくつかのコメントに統合し、統合された内容を首尾一貫したものに編集することを検討してください。

    他の人がフォローアップのコメントを投稿した後に古いコメントを編集する場合は、あなたの修正が気づかれない可能性があることに注意する必要があります。もし誤字脱字の修正でなければ、前のコメントで何かが変更されたことを示す新しいコメントを書くようにしてください。

    例えば、最初のコメントは最も重要なものです。スレッドが展開していく中で、自分が当初思っていたような状況ではないことに気付いた場合、最初の投稿を最新の理解を反映したものに編集すると、今後あなたの問題を読む人が何が起こっているのかをすぐに理解することができ、何十ものコメントを吟味する必要がなくなります。また、その投稿が編集されたことを示すのにも役立ちます。これにより、後からスレッドを読む人は、情報の流れにある種の不連続性がある理由を理解することができます。

    アイテムのリストがあり、全体的な読みやすさが向上する場合は、箇条書きやアイテムを使用してください。

    BartModel`や`generate`などのクラス名や関数名を参照する際には、バックティックを使うと目立ち、読者の理解速度が向上します。

    また、イタリックやボールドを多用すると、かえって読みにくくなりますのでご注意ください。

12. 特定のスレッドや別のイシューの特定のコメントを相互に参照する場合、イシューのリンクではなく、必ずその特定のコメントにリンクしてください。後者を使用すると、どの特定のコメントを参照しているのかを見つけるのが非常に困難になる可能性があります。

    特定のコメントへのリンクを取得するには、ブラウザのロケーションバーからURLをコピーするのではなく、コメントの右上にある「`...`」アイコンをクリックし、「Copy Link」を選択してください。

    例えば、最初のリンクは課題へのリンク、2番目のリンクは同じ課題の特定のコメントへのリンクです:

    1. https://github.com/huggingface/transformers/issues/9257
    2. https://github.com/huggingface/transformers/issues/9257#issuecomment-749945162


13. 前回のコメントに返信する場合は、自分のコメントだけを入れて返信しても全く問題ありません。読者はここで情報の流れを追うことができます。

    しかし、何コメントか前のコメントに返信する場合は、関連する行だけを引用するのが良い方法です。引用には`>`を使いますが、メニューを使ってもできます。例えば、エディターボックスは次のようになります:

    ```
    > How big is your gpu cluster?

    Our cluster is made of 256 gpus.
    ```

    複数のコメントに対して回答する場合は、それぞれのコメントの該当部分を引用してから回答してください。1つのコメントで複数の返信をする人もいれば、別のコメントに分けて返信する人もいます。どちらでも構いません。後者の方法は、特定のコメントへのリンクに役立ちます。

一般的に、何が最も効果的かを知るための最良の方法は、他の人が投稿した問題から学ぶことです。どの問題が素晴らしい反応を得て、どの問題がほとんど反応を得られないかを見て、素晴らしい反応を得た投稿者が、そうでない投稿者と何が違っていたかを観察するのです。

このやや長い文書をお読みいただき、ありがとうございました。これらは絶対的なルールではありませんが、あなたが伝えようとしていることを理解し、問題を再現し、あなたが満足し、コミュニティ全体が利益を得られるように解決する機会を最大限にするための親切なアドバイスであると結論づけたいと思います。

このドキュメントを読んでも、方法や理由について疑問が残ったり、さらに詳しい説明が必要な場合は、遠慮なく[このスレッド](https://discuss.huggingface.co/t/how-to-request-support/3128)で質問してください。
