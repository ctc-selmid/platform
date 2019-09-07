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
- [各種IdPとの接続情報](https://github.com/ctc-selmid/platform/blob/master/Manual/aadb2c_config.md#%E5%90%84%E7%A8%AEidp%E3%81%A8%E3%81%AE%E6%8E%A5%E7%B6%9A%E6%83%85%E5%A0%B1)  
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

- 例 : 入力属性値にprefix_をつけて返却する  
```
<ClaimsTransformation Id="sampleFormatTransformation" TransformationMethod="FormatStringClaim">
  <InputClaims>
    <InputClaim ClaimTypeReferenceId="sampleStringAttribute1" TransformationClaimType="inputClaim" />
  </InputClaims>
  <InputParameters>
    <InputParameter Id="stringFormat" DataType="string" Value="prefix_{0}" />
  </InputParameters>
  <OutputClaims>
    <OutputClaim ClaimTypeReferenceId="sampleStringAttribute2" TransformationClaimType="outputClaim" />
  </OutputClaims>
</ClaimsTransformation>
```


#### UI定義（`ContentDefinitions`エレメント配下）  
参考情報（[公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/contentdefinitions)）  
本項目ではUIのテンプレートとローカライゼーションを行います。  
- UIテンプレートの定義
  - htmlテンプレートを作成し、Azure Storageへ格納します  
  - 参考情報（[公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/active-directory-b2c-ui-customization-custom)）
- ローカライゼーションの定義  
  - `Localization`エレメント配下に各言語に対応した`ContentDefinition`を用意し、`LocalizedResourcesReferences`に作成したコンテンツ定義の`LocalizedResourcesReferenceId`を指定します  
  - 参考情報（[公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/localization)）


#### 各種IdPとの接続情報（`ClaimsProviders`エレメント配下）  
基本的に以下の情報を設定することで外部IdPと連携します。  

| 設定項目 | 説明 | 取得元 | 設定箇所 |
|:---|:---|:---|:---|
| client_id | SELMIDをclient（外部IdPから見たアクセス元アプリケーション）として識別するためのID | 外部IdP | SELMID/USER_EXTENSION_BASE |
| client_secret | SELMIDを正しいclientとして認証するためのシークレット | 外部IdP | SELMID/管理コンソールのポリシーキー |
| redirect_uri | 外部IdPからの戻り先URL（SELMIDのURL） | SELMID<br>`https://yourtenant.b2clogin.com/yourtenant.onmicrosoft.com/oauth2/authresp`を使用 | 外部IdP |

以下の外部IdPとの接続に対応しています。（随時追加）  

| Identity Provider名 | プロトコル | 設定する情報 | 取得できる属性 | IdP側の設定手順 |
|:---|:---|:---|:---|:---|
| Facebook | OAuth2.0 | client_id<br>client_secret<br>scope<br>ClaimsEndpoint | issuerUserId<br>givenName<br>surname<br>displayName<br>email | [facebook for developers](https://developers.facebook.com/docs/apps?locale=ja_JP) |
| Twitter | OAuth1.0a | client_id<br>client_secret | issuerUserId<br>displayName<br>email | [twitter developer](https://developer.twitter.com/en/apps) |
| Google | OAuth2.0 | client_id<br>client_secret | issuerUserId<br>email<br>givenName<br>surname<br>displayName | [Google Developer Console](https://developers.google.com/identity/protocols/OAuth2?hl=ja) |
| LINE | OpenID Connect | client_id<br>client_secret<br>scope | issuerUserId<br>displayName<br>email<br>identityProviderAccessToken | [LINE Developer](https://developers.line.biz/ja/docs/line-login/web/integrate-line-login/) |
| Yahoo! JAPAN | OAuth2.0 | client_id<br>client_secret<br>scope | issuerUserId<br>displayName<br>email<br>givenName<br>surName | [Yahoo! ID連携](https://developer.yahoo.co.jp/yconnect/v2/) |
| Apple<br>*テスト実装 | OpenID Connect | client_id<br>client_secret<br>scope | issuerUserId<br>displayName<br>email<br> | [Sign in with Apple](https://developer.apple.com/sign-in-with-apple/) |


## USER_EXTENSION_USERJOURNEYS  
### 設定内容  
- ユーザジャーニー定義
  - アクション単位の動作フローを定義します  
#### ユーザジャーニー定義（`UserJourneys`エレメント配下）  
参考情報（[公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/userjourneys)）  

| 要素種別 | 定義項目 | 説明 |
|:---|:---|:---|
| 属性 | Id | UserJourneyの識別子 |
| 要素 | OrchestrationSteps | UserJourneyを構成するオーケストレーションステップの定義 |

OrchestrationsStepの構成要素

| 要素種別 | 定義項目 | 説明 |
|:---|:---|:---|
| 属性 | Order | 実行順序 |
| 属性 | Type | 実行するステップのタイプ<br>- ClaimsProviderSelection: IdP選択画面の表示<br>- CombinedSignInAndSignUp: サインアップ/サインイン画面の表示<br>- ClaimsExchange: ClaimsProviderと属性の交換<br>- SendClaims: id_tokenの発行 |
| 属性 | ContentDefinitionReferenceId | ClaimsProviderSelection, CombinedSignInAndSignUpの際に表示するコンテンツ定義 |
| 属性 | CpimIssuerTechnicalProfileReferenceId | SendClaimsの際に使うトークン定義 |
| 要素 | Preconditions | ステップを実行する条件 |
| 要素 | ClaimsProviderSelections | TargetClaimsExchangeIdに選択対象となるClaimsProviderのClaimsExchangeIdを指定 |
| 要素 | ClaimsExchanges | 属性交換を行うClaimsProviderのTechnicalProfileを指定 |

例 1: 外部IdPの選択画面を表示し、選択したIdPから属性を取得する  
```
<!-- IdP一覧の表示 -->
<OrchestrationStep Order="1" Type="CombinedSignInAndSignUp" ContentDefinitionReferenceId="api.signuporsignin">
  <ClaimsProviderSelections>
    <ClaimsProviderSelection TargetClaimsExchangeId="FacebookExchange" />
    <ClaimsProviderSelection TargetClaimsExchangeId="TwitterExchange" />
    <ClaimsProviderSelection TargetClaimsExchangeId="GoogleExchange" />
    <ClaimsProviderSelection TargetClaimsExchangeId="LINEExchange" />
    <ClaimsProviderSelection TargetClaimsExchangeId="YahooExchange" />
    <ClaimsProviderSelection TargetClaimsExchangeId="AppleExchange" />
    <ClaimsProviderSelection ValidationClaimsExchangeId="LocalAccountSigninEmailExchange" />
  </ClaimsProviderSelections>
  <ClaimsExchanges>
    <ClaimsExchange Id="LocalAccountSigninEmailExchange" TechnicalProfileReferenceId="SelfAsserted-LocalAccountSignin-Email" />
  </ClaimsExchanges>
</OrchestrationStep>
<!-- 選択したIdPから属性を取得する -->
<OrchestrationStep Order="2" Type="ClaimsExchange">
  <ClaimsExchanges>
    <ClaimsExchange Id="FacebookExchange" TechnicalProfileReferenceId="Facebook-OAUTH" />
    <ClaimsExchange Id="TwitterExchange" TechnicalProfileReferenceId="Twitter-OAUTH1" />
    <ClaimsExchange Id="GoogleExchange" TechnicalProfileReferenceId="Google-OAUTH" />
    <ClaimsExchange Id="LINEExchange" TechnicalProfileReferenceId="LINE-OIDC" />
    <ClaimsExchange Id="YahooExchange" TechnicalProfileReferenceId="YahooJAPAN-OAUTH" />
    <ClaimsExchange Id="AppleExchange" TechnicalProfileReferenceId="Apple-OIDC" />
    <ClaimsExchange Id="SignUpWithLogonEmailExchange" TechnicalProfileReferenceId="LocalAccountSignUpWithLogonEmail" />
  </ClaimsExchanges>
</OrchestrationStep>
```

Preconditionの構成要素

| 要素種別 | 定義項目 | 説明 |
|:---|:---|:---|
| 属性 | type | 条件のタイプ<br>- ClaimsExist: 属性が存在するか<br>- ClaimEquals: 属性が等しいか |
| 属性 | ExecuteActionsIf | 実行条件<br>- true: typeが真なら実行<br>- false: typeが偽なら実行 |
| 要素 | Value | 判定対象の属性 |
| 要素 | Action | 条件に合致した場合に実行するアクション<br>- SkipThisOrchestrationStep: ステップをスキップする |

- 参考）Preconditionを複数指定した場合は各条件のorが取られる  
例 2: objectIdが存在したらこのステップをスキップする  
```
<Preconditions>
  <Precondition Type="ClaimsExist" ExecuteActionsIf="true">
    <Value>objectId</Value>
    <Action>SkipThisOrchestrationStep</Action>
  </Precondition>
</Preconditions>
```


## USER_EXTENSION_RP_XX  
### 設定内容  
- アプリケーションとのインターフェイス定義  
  - id_tokenに含める属性を定義します  
#### アプリケーションとのインターフェイス定義  
参考情報（[公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/relyingparty)）  
