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
- やったこと：
- 結果：
- 気づき・疑問：
