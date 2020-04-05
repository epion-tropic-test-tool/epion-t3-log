#  Command

- Contents
  - [Information](#Information)
  - [Description](#Description)
  - [Flow List](#Flow-List)
  - [Command List](#Command-List)
  - [Configuration List](#Configuration-List)
  - [Message List](#Message-List)


## Information
ログ関連のコマンドを提供します。

- Name : `log`
- Custom Package : `com.epion_t3.log`

## Description
テスト実行時のログ関連の機能を提供します。

## Flow List

## Command List

|Name|Summary|Assert|Evidence|
|:---|:---|:---|:---|
|[LogExtractDuringTime](#LogExtractDuringTime)|ログの抽出を実行時間から行います。指定したログファイルから指定したコマンドの実行時間（開始〜終了の間）のログを抽出します。エビデンスを残すための手段となります。  ||X|

------

### LogExtractDuringTime
ログの抽出を実行時間から行います。指定したログファイルから指定したコマンドの実行時間（開始〜終了の間）のログを抽出します。エビデンスを残すための手段となります。
#### Command Type
- Assert : No
- Evidence : __Yes__

#### Functions
- ログファイルから実行時間分のみのログを抽出することが可能です。
- ログファイルは最終的に抽出された内容で上書きされます。
- 対象とするログファイルは事前にエビデンスとして取得している必要があります。

#### Structure
```yaml
commands : 
  id : コマンドのID
  command : 「LogExtractDuringTime」固定
  summary : コマンドの概要（任意）
  description : コマンドの詳細（任意）
  target : 対象のログファイルをエビデンス取得したFlowIDを指定 # (1)
  targetFlow : ログの抽出対象とする操作を行なったFlowID # (2)
  extractPattern : 時間の抽出パターン # (3)
  group : 時間の抽出パターンに対する対象グループ #(4)
  encoding : ログファイル読み込みエンコーディング #(4)

```

1. 読み込むログファイルを特定するために、エビデンス取得を行なったFlowIDを指定します。
1. ログの抽出を行うべき時間を特定するために利用する。試験対象に対してログを取得したい操作を行なったFlowIDを指定する。
1. ファイルを読み込み、１行ずつ時間の範囲内であるか判断を行います。その際に日付時間を抽出するための正規表現パターンを設定します。
1. 時間の抽出パターンでは正規表現のグループを使用します。その際に日付時間と認識するグループを指定します。デフォルトは「1」です。
1. ログファイルを読み込むエンコーディングの指定を行います。デフォルトは「UTF-8」です。

## Configuration List

## Message List

 Command output messages.

|MessageID|MessageContents|
|:---|:---|
|com.epion_t3.log.err.9001|対象（target）は必須です.|
|com.epion_t3.log.err.9004|日付解析にてエラーが発生しました.抽出文字列：{0}、パターン：{1}|
|com.epion_t3.log.err.9003|抽出パターンは必須です.|
|com.epion_t3.log.err.9002|値（value）は必須です.|
