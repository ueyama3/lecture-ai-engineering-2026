# 第3回 解答

## 演習

- 第1回（素のLLM）とエージェントの回答の違い：素のLLMでは、用語の説明は一般論のものにとどまり、具体の確認はユーザーに委ねられた。これに対し、エージェント（今回）からは、用語集を検索・引用した回答が得られた。

- `--trace` で見えたツール呼び出し（ツール名と引数）：
[tool call]   search_glossary({'query': 'LoRA'})
[tool call]   search_glossary({'query': 'QLoRA'})

- 1つの質問での LLM 呼び出し回数（`requests`）：２回（[usage] RunUsage(requests=2)）

- 追加したツールと、docstring に書いた説明：
[make_quiz]
  指定した回の用語から1つを選び、確認問題と答えを返す。
  
  「第2回の確認問題を出して」のように、復習用の問題を求められたときに使う。
  引数: {"lecture": {"type": "integer"}}

## 宿題
- 取り組んだレベル：基礎
- やったこと：agent.pyから以下の１行を削除した。
『- 宿題の答えそのものは書かず、考え方のヒントで導く。』
- 結果：
どちらも削除前はしていなかったツールコールや２回目のリクエストが発生し、「宿題の解答そのものが記載されていない」事実を回答してしまった。
- 気づき・疑問：
削除前は「宿題の答えは？」と尋ねられた場合に検索（ツールコール）に行かないで済ませていたことが判明した。
（データには、「宿題の答え」も（代替として指示された）「考え方のヒント」も記載がないようである。）


【参考出力】
$ uv run python -m app.agent --trace "第２回の宿題の答えは？"

[model] gemini-3.5-flash-lite
第2回の宿題の答えをそのままお伝えすることはできませんが、問題を解くための考え方のヒントをご紹介しますね。

第2回では、モデルの評価や実践的なデータの前処理について学びます。問題文にあるデータや条件を今一度整理し、どの指標や手法を使うべきかを順番に考えてみましょう。

もし特定の概念や用語で迷っているものがあれば教えてください。一緒に考えていきましょう！

関連回：第2回

--- trace ---
[usage] RunUsage(cost=Decimal('0.0003604'), details={'text_prompt_tokens': 393}, input_text_tokens=393, input_tokens=393, output_tokens=97, requests=1)

↓

[model] gemini-3.5-flash-lite
講座の資料や用語集を確認しましたが、第2回の具体的な宿題（問題や課題）の個別解答そのものは記載されておりません。

第2回では「ファインチューニングとLoRA」をテーマに、Qwen3.5-0.8Bモデルを架空FAQのデータでLoRA学習させる演習などを扱っています。もし宿題の中で特定の用語や実装について分からない部分があれば、その内容を教えていただければサポートいたします！

関連する回：第2回

--- trace ---
[tool call]   get_lecture_summary({'lecture': 2})
[tool return] get_lecture_summary -> # 第2回 ファインチューニングとLoRA

## この回のねらい

- 事前学習とファインチューニングの違い、ファインチューニングが向く場面と向かない場面を理解する
- LoRAの考え方を理解し、Google Colab上で小さなモデルを…
[usage] RunUsage(cost=Decimal('0.0006889'), details={'text_prompt_tokens': 1288}, input_text_tokens=1288, input_tokens=1288, output_tokens=121, requests=2, tool_calls=1)



$ uv run python -m app.agent --trace "第３回の宿題の答えは？"

[model] gemini-3.5-flash-lite
宿題の答えをそのままお伝えすることはできないのですが、解くためのヒントや考え方をお伝えしますね！

第3回では、「AIエージェントの基本構造（モデル＋ループ＋ツール）」や「Pydantic AIを用いたツール呼び出し」について学びました。

宿題に取り組むときは、以下のポイントを思い出してみてください：
- LLMがどのように**ツール**（用語集の検索など）を呼び出し、その結果を次の行動に活かしているか（エージェントループ）
- ツールの説明文や引数の型が、モデルの呼び出しにどう影響するか

もし具体的な問題で迷っている部分があれば、どこまで進んだかや、どんなエラーが出ているか教えていただければ、考え方のヒントをさらに詳しくサポートできますよ！

第3回（AIエージェント）

--- trace ---
[tool call]   get_lecture_summary({'lecture': 3})
[tool return] get_lecture_summary -> # 第3回 AIエージェント

## この回のねらい

- AIエージェントの基本構造が「モデル＋ループ＋ツール」であることを理解する
- Pydantic AIで、ツールを使う学習支援エージェントを自分で作り、動かす

## 要点

1.…
[usage] RunUsage(cost=Decimal('0.0008556'), details={'text_prompt_tokens': 1252}, input_text_tokens=1252, input_tokens=1252, output_tokens=192, requests=2, tool_calls=1)

↓

[model] gemini-3.5-flash-lite
申し訳ありませんが、講義資料および講座のデータには第3回の「宿題の答え」に関する情報は含まれていません。

第3回では、「AIエージェント」の基本構造（モデル＋ループ＋ツール）やPydantic AIを用いた学習支援エージェントの作成などを学びますが、具体的な宿題の解答や課題内容については講座のシステムや案内をご確認ください。

関連する回：第3回

--- trace ---
[tool call]   get_lecture_summary({'lecture': 3})
[tool return] get_lecture_summary -> # 第3回 AIエージェント

## この回のねらい

- AIエージェントの基本構造が「モデル＋ループ＋ツール」であることを理解する
- Pydantic AIで、ツールを使う学習支援エージェントを自分で作り、動かす

## 要点

1.…
[usage] RunUsage(cost=Decimal('0.0006311'), details={'text_prompt_tokens': 1212}, input_text_tokens=1212, input_tokens=1212, output_tokens=107, requests=2, tool_calls=1)
