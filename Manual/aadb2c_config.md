# ID基盤の構成  
Azure Active Directory B2C(以下、Azure AD B2C）のカスタムポリシーを利用してSELMIDの振る舞いの設定を行います。  

## カスタムポリシーの構造  
以下のカスタムポリシーが提供されます。

| ポリシー名 | 契約企業様による編集可否 | 定義内容 |
|:---|:---|:---|
| BASE | 不可 | 基本動作に必要な定義 |
| SELMID_EXTENSION | 不可 | CTC拡張機能の定義 |
| USER_EXTENSION_BASE | 可 | 契約企業様毎の設定（スキーマ、UI定義、各種IdPの接続情報） |
| USER_EXTENSION_USERJOURNEYS | 可 | 契約企業様毎のユーザジャーニーの設定 |
| USER_EXTENSION_RP_XX | 可 | 契約企業様毎のアプリケーションとの連携設定（呼び出すポリシー単位で作成） |
- 編集不可となっているポリシーの修正～アップロードを行った場合、動作の保証がされません。  
- 基本的に上位のポリシーを下位のポリシーがオーバーライドします。  

## USER_EXTENSION_BASE  
### 設定内容  
- スキーマ（カスタム属性）  
  - 標準外の属性を定義します
- 属性変換ルール定義  
  - 属性値を変換する関数を定義します  
- UI定義  
  - 各種画面テンプレートを定義します
- 各種IdPとの接続情報  
  - 外部IdP（SNS等）との接続情報（client_id, client_secret, 取得する属性等）を定義します
  - 基盤本体のIDデータベースとのインターフェイス（書き込み・読み込みする属性）を定義します

## USER_EXTENSION_USERJOURNEYS  
### 設定内容  
- ユーザジャーニー定義
  - アクション単位の動作フローを定義します  

## USER_EXTENSION_RP_XX  
### 設定内容  
- アプリケーションとのインターフェイス定義  
  - id_tokenに含める属性を定義します  

# 各構成内容  
## USER_EXTENSION_BASE  
### スキーマ定義  
- 参考情報（[公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/claimsschema)）  
- ClaimType IdのPrefixにより永続させる（Azure AD B2Cのデータベースのスキーマ拡張と属性値の保持）ことが出来るかどうかが決定されます  
  - prefixなし : 非永続（カスタムポリシー内のみで利用可能）  
  - extension_ : 永続化（Azure AD B2Cのデータベース内に保存可能）  
- 例 1: 文字列属性（非永続）の定義  
```
<ClaimType Id="sampleStringAttribute1">
   <DisplayName>sample string attribute1</DisplayName>
   <DataType>string</DataType>
   <UserInputType>TextBox</UserInputType>
</ClaimType>
```
- 例 2: 文字列属性（永続）の定義  
```
<ClaimType Id="extension_samplePersistentAttribute">
   <DisplayName>sample persistent attribute</DisplayName>
   <DataType>string</DataType>
</ClaimType>
```

### 属性変換ルール定義  
参考情報（[公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/claimstransformations)）  
### UI定義  
参考情報（[公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/contentdefinitions)）  
### 各種IdPとの接続情報  

## USER_EXTENSION_USERJOURNEYS  
### ユーザジャーニー定義  
参考情報（[公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/userjourneys)）  

## USER_EXTENSION_RP_XX  
### アプリケーションとのインターフェイス定義  
参考情報（[公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/relyingparty)）  
