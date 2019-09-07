# ID基盤の構成  
Azure Active Directory B2C(以下、Azure AD B2C）のカスタムポリシーを利用してSELMIDの振る舞いの設定を行います。  

## カスタムポリシーの構造  
以下のカスタムポリシーが提供されます。

| ポリシー名 | 契約企業様による編集可否 | 定義内容 |
|:---|:---|:---|
| BASE | 不可 | 基本動作に必要な定義 |
| SELMID_EXTENSION | 不可 | CTC拡張機能の定義 |
| [USER_EXTENSION_BASE](https://github.com/ctc-selmid/platform/blob/master/Manual/aadb2c_config.md#user_extension_base) | 可 | 契約企業様毎の設定（スキーマ、UI定義、各種IdPの接続情報） |
| [USER_EXTENSION_USERJOURNEYS](https://github.com/ctc-selmid/platform/blob/master/Manual/aadb2c_config.md#user_extension_userjourneys) | 可 | 契約企業様毎のユーザジャーニーの設定 |
| [USER_EXTENSION_RP_XX](https://github.com/ctc-selmid/platform/blob/master/Manual/aadb2c_config.md#user_extension_rp_xx) | 可 | 契約企業様毎のアプリケーションとの連携設定（呼び出すポリシー単位で作成） |
- 編集不可となっているポリシーの修正～アップロードを行った場合、動作の保証がされません。  
- 基本的に上位のポリシーを下位のポリシーがオーバーライドします。  

# 各構成内容  
※すべての設定可能項目を記載している訳ではありません。公式ドキュメントに記載されている設定項目はご利用いただけますが詳細はお問い合わせください。  
## USER_EXTENSION_BASE  
### 設定内容  
- [スキーマ（カスタム属性）](https://github.com/ctc-selmid/platform/blob/master/Manual/aadb2c_config.md#%E3%82%B9%E3%82%AD%E3%83%BC%E3%83%9E%E5%AE%9A%E7%BE%A9claimsschema%E3%82%A8%E3%83%AC%E3%83%A1%E3%83%B3%E3%83%88%E9%85%8D%E4%B8%8B)  
  - 標準外の属性を定義します
- [属性変換ルール定義](https://github.com/ctc-selmid/platform/blob/master/Manual/aadb2c_config.md#%E5%B1%9E%E6%80%A7%E5%A4%89%E6%8F%9B%E3%83%AB%E3%83%BC%E3%83%AB%E5%AE%9A%E7%BE%A9claimstransformations%E3%82%A8%E3%83%AC%E3%83%A1%E3%83%B3%E3%83%88%E9%85%8D%E4%B8%8B)  
  - 属性値を変換する関数を定義します  
- [UI定義](https://github.com/ctc-selmid/platform/blob/master/Manual/aadb2c_config.md#ui%E5%AE%9A%E7%BE%A9contentdefinitions%E3%82%A8%E3%83%AC%E3%83%A1%E3%83%B3%E3%83%88%E9%85%8D%E4%B8%8B)  
  - 各種画面テンプレートを定義します
- 各種IdPとの接続情報  
  - 外部IdP（SNS等）との接続情報（client_id, client_secret, 取得する属性等）を定義します
  - 基盤本体のIDデータベースとのインターフェイス（書き込み・読み込みする属性）を定義します

#### スキーマ定義(`ClaimsSchema`エレメント配下)  
- 参考情報（[公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/claimsschema)）  
- 注意点) ClaimType IdのPrefixにより永続させる（Azure AD B2Cのデータベースのスキーマ拡張と属性値の保持）ことが出来るかどうかが決定されます  
  - prefixなし : 非永続（カスタムポリシー内のみで利用可能）  
  - extension_ : 永続化（Azure AD B2Cのデータベース内に保存可能）  
- 定義内容  

| 要素種別 | 定義項目 | 説明 |
|:---|:---|:---|
| 属性 | Id | Claim（属性）の識別子 |
| 要素 | Displayname | Claimの表示名 |
|| DataType | 属性の型<br>- string: 文字列<br>- boolean: ブール値<br>- date: 日付型<br>- datetime: 日付時刻型<br>- int: int型<br>- long: long型<br>- stringCollection: 文字列コレクション型<br>- alternativeSecurityIdCollection: 外部IdPの識別子コレクション |
|| Mask | 値のマスクパターン |
|| UserHelpText | ヘルプテキスト |
|| UserInputType | ユーザが値を入力する場合に使うフォームの型<br>- TextBox: テキストボックス<br>- EmailBox: メールアドレス<br>- Password: パスワード<br>- DateTimeDropdown: 日付と時刻の選択<br>- RadioSingleSelect: ラジオボタン<br>- DropdownSingleSelect: ドロップダウンリスト（単一選択）<br>- CheckboxMultiSelect: チェックボックス（複数選択）<br>- Readonly: 表示のみ<br>- Paragraph:メッセージ表示  |
|| Restriction | 入力値を制限する際に使う正規表現 |

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


#### 属性変換ルール定義（`ClaimsTransformations`エレメント配下）  
参考情報（[公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/claimstransformations)）　 
SELMIDでは以下の属性変換ルールをビルトインしています。まずはビルトインルールで要件が満たせるかどうかご検討ください。  

| ルール名 | 動作概要 | 入力 | 出力 |
|:---|:---|:---|:---|
| CreateOtherMailsFromEmail | メールアドレスをotherMailsコレクションに加えます | email | otherMails |
| CreateRandomUPNUserName | GUID形式でupnUserNameを生成します | - | upnUserName |
| CreateUserPrincipalName | cpim_{upnUserName}@{tenant名}形式でuserPrincipalName（Azure AD B2C内部の識別子）を生成します<br>例）cpim_32407727-a73a-4944-9fdb-54cf4d755ddf@yourtenant.onmicrosoft.com | upnUserName | userPrincipalName |
| CreateAlternativeSecurityId | 外部IdPの識別子からalternativeSecurityIdを生成します | issuerUserId<br>identityProvider | alternativeSecurityId |
| AssertAccountEnabledIsTrue | accountEnabled属性がtrueならtrueを返却します | accountEnabled | True/False |
| CreateUserIdForMFA | 多要素認証用のuserId属性を生成します<br>{objectId}@{tenant名}の形式 | objectId | userIdForMFA |
| CopyEmailToReadOnly | email属性の値をreadOnlyEmail属性にコピーします | email | readOnlyEmail |


#### UI定義（`ContentDefinitions`エレメント配下）  
参考情報（[公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/contentdefinitions)）  
本項目ではUIのテンプレートとローカライゼーションを行います。  
- UIテンプレートの定義
  - htmlテンプレートを作成し、Azure Storageへ格納します  
  - 参考情報（[公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/active-directory-b2c-ui-customization-custom)）
- ローカライゼーションの定義  
  - `Localization`エレメント配下に各言語に対応した`ContentDefinition`を用意し、`LocalizedResourcesReferences`に作成したコンテンツ定義の`LocalizedResourcesReferenceId`を指定します  
  - 参考情報（[公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/localization)）


#### 各種IdPとの接続情報  

## USER_EXTENSION_USERJOURNEYS  
### 設定内容  
- ユーザジャーニー定義
  - アクション単位の動作フローを定義します  
#### ユーザジャーニー定義  
参考情報（[公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/userjourneys)）  

## USER_EXTENSION_RP_XX  
### 設定内容  
- アプリケーションとのインターフェイス定義  
  - id_tokenに含める属性を定義します  
#### アプリケーションとのインターフェイス定義  
参考情報（[公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/relyingparty)）  
