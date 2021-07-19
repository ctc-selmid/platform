# SELMID_EXTENSION_V3
 - CTC拡張機能の関する各定義を行うファイル。
 - バージョン：3

## <a id="claimtype"></a> ClaimType定義(`ClaimsSchema`エレメント配下)
| ID | 概要 | 設定 |
|:---|:---|:---|
| readOnlyEmail | 読み取り用メールアドレス | 属性：Mask、Type：Regex、Regex： (?&lt;=..).(?=.*..$)、値： * |
| givenName | Azure ADユーザープロファイルの属性 [公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/user-profile-attributes) |
| surname | Azure ADユーザープロファイルの属性 [公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/user-profile-attributes) |
| identityProviderAccessToken | IdPから取得したアクセストークン |
| oidc_display | OIDCパラメータ |
| oidc_prompt | OIDCパラメータ |
| oidc_max_age | OIDCパラメータ |
| oidc_ui_locales | OIDCパラメータ |
| oidc_id_token_hint | OIDCパラメータ |
| oidc_login_hint | OIDCパラメータ |
| oidc_acr_values | OIDCパラメータ |
| oidc_redirect_uri | OIDCパラメータ |
| bot_prompt | LINEログイン：LINE公式アカウントを友だち追加するオプション |
| termsOfUseConsentChoice | 規約への同意チェックボックス |
| termsOfUseConsentCurrentVersion | 規約への同意：現在の最新バージョン |
| termsOfUseConsentRequired | 規約への同意：同意が必要か |
| extension_termsOfUseConsentDateTime | 規約への同意：同意取得時刻 |
| extension_termsOfUseConsentVersion | 規約への同意：同意取得時のバージョン |
| userMessage | REST API：処理結果メッセージ |
| status | REST API：処理結果ステータス（HTTP CODE） |
| errorMessage | エラーメッセージ |
| ipaddress | IPアドレス |
| capy_private_key | CAPY用定義：Privateキー |
| submit.capy_answer | CAPY用定義：パズルキャプチャのcapy_answer |
| submit.capy_challengekey | CAPY用定義：パズルキャプチャのcapy_challengekey |
| capy_puzzle_result | CAPY用定義：パズルキャプチャの結果 |
| capy_puzzle_reason | CAPY用定義：パズルキャプチャの理由 |
| capy_puzzle_error_message | CAPY用定義：パズルキャプチャのエラーメッセージ |
| capy_riskbase_key | CAPY用定義：リスクベース認証のキー |
| capy_userId | CAPY用定義：リスクベース認証のcapy_data生成時のuserId |
| capy_data | CAPY用定義：リスクベース認証のcapy_data |
| capy_risk_result | CAPY用定義：リスクベース認証の結果 |
| capy_risk_level | CAPY用定義：リスクベース認証のレベル  |
| capy_risk_reason | CAPY用定義：リスクベース認証の理由（複数存在する場合は1件目が設定） |
| capy_risk_reasons | CAPY用定義：リスクベース認証の理由（複数存在する場合は","区切り） |
| capy_risk_reasons_collection | CAPY用定義：capy_risk_reasonsのCollection型  |
| debug_capy_risk_reasons | CAPY用定義：リスクベース認証のデバッグ用。強制的に返却するdebug_capy_risk_reasonsを指定（複数指定する場合は","区切り）  |
| capy_blacklist_key | CAPY用定義：リアルタイムブラックリストのキー |
| capy_ipaddress | CAPY用定義：リアルタイムブラックリストのipaddress |
| capy_black_types | CAPY用定義：リアルタイムブラックリストの評価結果のtypes(複数の場合はカンマ区切り)  |
| capy_black_result | CAPY用定義：リアルタイムブラックリストの評価結果のresult  |
| capy_black_value | CAPY用定義：リアルタイムブラックリストの評価結果のvalue  |
| userIdentity | [Deprecated]アカウントリンクV2用のuserIdentity。今後は[alternativeSecurityId](./aadb2c_b2c_base.md#alternativesecurityid)を利用してください。 |
| userIdentities | [Deprecated]アカウントリンクV2用のuserIdentities。今後は[alternativeSecurityIds](./aadb2c_b2c_base.md#alternativesecurityids)を利用してください。 |
| userIdentityToLink | [Deprecated]アカウントリンクV2用のuserIdentity。今後は[alternativeSecurityIdToLink](./aadb2c_b2c_base.md#alternativesecurityidtolink)を利用してください。 |
| userIdentitiesToLink | [Deprecated]アカウントリンクV2用のuserIdentity。V3では未使用。 |
| otp | custom sender用定義：ワンタイムパスワード  |
| verificationCode | custom sender用定義：ワンタイムパスワード検証用入力  |
| sendGridReqBody | custom sender用定義：SendGrid APIリクエストBody  |
| lang_ja | 多言語用定義：ブラウザ設定がjaか  |
| lang_en | 多言語用定義：ブラウザ設定がenか  |
| SELMID個別機能属性定義  |
| selmid_capy_riskbase_enabled | リスクベース認証：有効設定（ON：有効、OFF：無効 or 定義なし）  |
| selmid_issuerUserId | リスクベース認証：追加認証した際のissuerUserId(email)  |
| selmid_identity_provider |  (本人確認等を行う)Identity Provider |
| selmid_idp_access_token |  (本人確認等を行う)IdPの access token |
| selmid_result |  (本人確認API等の) 実行結果 |
| selmid_docomo_endpoint_url | 本人確認API属性用定義：ドコモ本人確認アシストAPI URL |
| selmid_docomo_client_id |  本人確認API属性用定義：dアカウント・コネクト client_id |
| selmid_docomo_client_secret |  本人確認API属性用定義：dアカウント・コネクト client_secret |
| selmid_docomo_result_code |  本人確認API属性用定義：ドコモ本人確認アシストAPI 処理結果コード |
| selmid_docomo_mb_result |  本人確認API属性用定義：ドコモ本人確認アシストAPI 処理結果の戻り値（処理結果コード”10FU”の場合のみ） |
| selmid_docomo_mb_guidancecode |  本人確認API属性用定義：ドコモ本人確認アシストAPI HTTP エラーコード。異常時のみ。 |
| selmid_docomo_httpMessage |  本人確認API属性用定義：ドコモ本人確認アシストAPI HTTP エラー内容。異常時のみ。 |
| selmid_docomo_moreInformation |  本人確認API属性用定義：ドコモ本人確認アシストAPI エラー情報。異常時のみ。 |
| selmid_kddi_endpoint_url | 本人確認API属性用定義：KDDI本人確認支援サービスAPI URL |
| selmid_kddi_api_key | 本人確認API属性用定義：KDDI本人確認支援サービスAPI KDDI-API-KEY |
| selmid_kddi_cp_id | 本人確認API属性用定義：KDDI本人確認支援サービスAPI 加盟店ID |
| selmid_kddi_service_id | 本人確認API属性用定義：KDDI本人確認支援サービスAPI 加盟店ID |
| selmid_kddi_status | 本人確認API属性用定義：KDDI本人確認支援サービスAPI レスポンスステータス |
| selmid_kddi_result_code | 本人確認API属性用定義：KDDI本人確認支援サービスAPI 結果に関するコード |
| selmid_kddi_error_result_code | 本人確認API属性用定義：KDDI本人確認支援サービスAPI エラー結果に関するコード。異常時のみ。 |
| selmid_kddi_error_message | 本人確認API属性用定義：KDDI本人確認支援サービスAPI エラーメッセージ。異常時のみ。 |
| selmid_totp_otpauth_url | TOTP用定義：登録時のアプリ読み込み用QRコードに設定する値（テキスト） |
| selmid_totp_secret_code | TOTP用定義：登録時のアプリがQRを読めない場合のテキストコード |
| selmid_totp_code | TOTP用定義：登録時のアプリで生成されたワンタイムコード |
| selmid_totp_issuer | TOTP用定義：発行者（サービス名。認証アプリに表示） |
| selmid_totp_encryption_secret_key | TOTP用定義：HMAC処理で利用されるシークレット |
| selmid_totp_error_message | TOTP用定義：エラーメッセージ |
| extension_selmid_totp_secret_key | TOTP用定義：拡張属性 シークレットキー(RESTAPIで生成) |
| extension_selmid_totp_timestepmatched | TOTP用定義：拡張属性 ユーザーが最後に認証成功した認証コード。（現在入力されているコードが、既に入力されているものではないかを確認する用）|

## <a id="claimstransformations"></a>属性変換ルール定義（`ClaimsTransformations`エレメント配下）
| ID | 動作概要 | 入力 | 出力 |
|:---|:---|:---|:---|
| GetNewUserAgreeToTermsOfUseConsentDateTime | 規約への同意の現在日時を取得します | - | extension_termsOfUseConsentDateTime |
| IsTermsOfUseConsentRequiredForDateTime | 新しい規約への同意が必要かどうかの判別します。日時で比較する場合用 | extension_termsOfUseConsentDateTime<br>termsOfUseTextUpdateDateTime(Valueで比較対象となる日時を指定) | termsOfUseConsentRequired |
| SetCurrentTermsOfUseVersion | 規約への同意の現在のバージョン（最新）を設定します | Valueで最新のバージョンを指定する | termsOfUseConsentCurrentVersion |
| GetCurrentTermsOfUseVersion | 規約への同意の現在のバージョン（最新）を取得します | termsOfUseConsentCurrentVersion | extension_termsOfUseConsentVersion |
| IsTermsOfUseConsentRequiredForVersion | 新しい規約への同意が必要かどうかの判別します。バージョンで比較する場合 | termsOfUseConsentCurrentVersion<br>extension_termsOfUseConsentVersion | termsOfUseConsentRequired |
| CreateCapyUserId | リスクベース認証用のCapyUserIdを作成します | objectId | capy_userId |
| ConvertCapyRiskReasonsToCollection | capy_risk_reasons（","区切り）をCollection型に変換します | capy_risk_reasons | capy_risk_reasons_collection |
| CreateUserIdentity | [Deprecated]ソーシャルアカウントのissuerUserIdとissuerからuserIdentityを作成します。今後は[CreateAlternativeSecurityId](./aadb2c_b2c_base.md#createalternativesecurityid)を利用してください。 | issuerUserId<br>identityProvider | userIdentity |
| CreateUserIdentityToLink | [Deprecated]ソーシャルアカウントのissuerUserIdとissuerからuserIdentityを作成（リンク用）します。今後は[CreateAlternativeSecurityIdToLink](./aadb2c_b2c_base.md#createalternativesecurityidtolink)を利用してください。 | issuerUserIdToLink<br>issuerToLink | userIdentityToLink |
| AppendUserIdentity | [Deprecated]userIdentities コレクションに userIdentity を追加します。今後は[AppendAlternativeSecurityId](./aadb2c_b2c_base.md#appendalternativesecurityid)を利用してください。 | userIdentity<br>userIdentities | userIdentities |
| AppendUserIdentityToLink | [Deprecated]userIdentities コレクションに userIdentityToLink を追加します。今後は[AppendAlternativeSecurityIdToLink](./aadb2c_b2c_base.md#appendalternativesecurityidtolink)を利用してください。 | userIdentityToLink<br>userIdentities | userIdentities |
| AppendUserIdentitiesToLink | [Deprecated]userIdentitiesToLink コレクションに userIdentityToLink を追加します | userIdentityToLink<br>userIdentitiesToLink | userIdentitiesToLink |
| RemoveUserIdentityFromCollectionByIssuer | [Deprecated]userIdentities コレクションからissuerToUnlinkを削除します。今後は[RemoveAlternativeSecurityFromCollectionByIssuer](./aadb2c_b2c_base.md#removealternativesecurityfromcollectionbyissuer)を利用してください。 | issuerToUnlink<br>userIdentities | userIdentities |
| ExtractIssuers | [Deprecated]ユーザーに関連付けられたソーシャル ID プロバイダのリストを抽出します。今後は[ExtractIssuersFromExtractTargetAlternativeSecurityIds](./aadb2c_b2c_base.md#extractissuersfromextracttargetalternativesecurityids)を利用してください。 | userIdentities | issuers |
| GenerateSendGridRequestBodyForOTP | [Deprecated]OTP用メール本文を生成します。今後は[GenerateSendGridRequestBodyForGeneralOTP](./aadb2c_selmid_extension.md#generatesendgridrequestbodyforgeneralotp)を利用してください。 | email<br>otp<br>lang_ja<br>lang_en | sendGridReqBody |
| <a id="generatesendgridrequestbodyforgeneralotp"/>GenerateSendGridRequestBodyForGeneralOTP | OTP用メール本文を生成します | otp<br>lang_ja<br>lang_en | sendGridReqBody |
| GenerateSendGridRequestBodyForMfaOTP | MFA OTP用メール本文を生成します | otp<br>lang_ja<br>lang_en | sendGridReqBody |
| GenerateSendGridRequestBodyForWelcome | Welcome用メール本文を生成します | otp<br>lang_ja<br>lang_en | sendGridReqBody |
| GenerateSendGridRequestBodyForPasswordChange | Password Change用メール本文を生成します。 | otp<br>lang_ja<br>lang_en | sendGridReqBody |
| AssertReadOnlyEmailAreEqual | 読み取り用メールアドレスが画面で変更されていないかチェックします(MFA OTP用) | otp<br>email | - |
| IsJapanese | ブラウザの言語設定が「ja」かを判断します | Culture | lang_ja |
| IsEnglish | ブラウザの言語設定が「en」かを判断します | Culture | lang_en |

## <a id="contentdefinitions"></a> UI定義（`ContentDefinitions`エレメント配下）
| ID | 概要 | DataUri |
|:---|:---|:---|
| api.selfasserted.tou | 利用規約を表示する画面 | urn:com:microsoft:aad:b2c:elements:contract:selfasserted:2.1.1 |
| api.selfasserted.makecapydataforriskbases | リスクベース認証 Capyデータ作成画面 | urn:com:microsoft:aad:b2c:elements:contract:selfasserted:2.1.1 |
| api.localaccountsignupwithpuzzle | ローカルアカウントのサインアップ画面（パズルキャプチャ付き） | urn:com:microsoft:aad:b2c:elements:contract:selfasserted:2.1.1 |
| api.selfasserted.totp.regist | TOTP登録画面（QRコード読み取り/テキストコード入力を行い、認証コードを入力します） | urn:com:microsoft:aad:b2c:elements:contract:selfasserted:2.1.1 |
| api.selfasserted.totp.verify| TOTP検証画面 | urn:com:microsoft:aad:b2c:elements:contract:selfasserted:2.1.1 |

## <a id="displaycontrols"></a> DisplayControl定義（`DisplayControls`エレメント配下）
| ID | 概要 | DisplayClaims | OutputClaims | Actions |
|:---|:---|:---|:---|:---|
| emailVerificationWidget | [Deprecated]Custom Senderを使ったOTP送信＆確認コントロール。今後は[emailVerificationControl](./aadb2c_b2c_base.md#emailverificationcontrol)を利用してください。 | email<br>verificationCode | email | <table><tr><th>id</th><th>ValidationClaimsExchange</th></tr><tr><td rowspan=2>SendCode</td><td>GenerateOtp</td></tr><tr><td>VerifyCode</td></tr><tr><td>VerifyOtp</td><td>GenerateOtp</td></tr></table> |
| <a id="emailverificationcontrol"/>emailVerificationControl | Custom Senderを使ったOTP送信＆確認コントロールです | verificationCode | - | <table><tr><th>id</th><th>ValidationClaimsExchange</th></tr><tr><td rowspan=2>SendCode</td><td>GenerateGeneralOtp</td></tr><tr><td>SendGeneralOtp</td></tr><tr><td>VerifyCode</td><td>VerifyGeneralOtp</td></tr></table> |
| mfaEmailVerificationControl | Custom Senderを使ったMFA OTP送信＆確認コントロールです | verificationCode | - | <table><tr><th>id</th><th>ValidationClaimsExchange</th></tr><tr><td rowspan=2>SendCode</td><td>GenerateMfaOtp</td></tr><tr><td>SendMfaOtp</td></tr><tr><td>VerifyCode</td><td>VerifyMfaOtp</td></tr></table> |


## 各種IdP接続定義（`ClaimsProviders`エレメント配下）
### facebook接続定義（Domain：facebook.com）
| ID | 概要 | Metadata | 入力 | 出力 | IncludeTechnicalProfile |
|:---|:---|:---|:---|:---|:---|
| Facebook-OAUTH-Base | 接続の共通定義 | - | - | issuerUserId<br>givenName<br>surname<br>displayName<br>email<br>identityProvider<br>authenticationSource | - |
| Facebook-OAUTH | [Deprecated]接続定義v1。今後は[Facebook-OAUTH-SignIn-v3](./aadb2c_selmid_extension.md#idp_facebook-oauth-signin-v3)を利用してください。 | - | - | - | Facebook-OAUTH-Base |
| Facebook-OAUTH-SignIn | [Deprecated]接続定義v2。今後は[Facebook-OAUTH-SignIn-v3](./aadb2c_selmid_extension.md#idp_facebook-oauth-signin-v3)を利用してください。 | - | - | - | Facebook-OAUTH-Base |
| <a id="idp_facebook-oauth-signin-v3"/>Facebook-OAUTH-SignIn-v3 | 接続定義v3 | - | - | - | Facebook-OAUTH-Base |
| Facebook-OAUTH-Link-Base | アカウントリンクの共通定義 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimTypeOnWhichToEnable</td><td>issuers</td></tr><tr><td>ClaimValueOnWhichToEnable</td><td>facebook.com</td></tr></table> | - | issuerUserIdToLink<br>issuerToLink | Facebook-OAUTH-Base |
| Facebook-OAUTH-Link | [Deprecated]アカウントリンク定義v2。今後は[Facebook-OAUTH-Link-v3](./aadb2c_selmid_extension.md#idp_facebook-oauth-link-v3)を利用してください。 | - | - | - | Facebook-OAUTH-Link-Base |
| <a id="idp_facebook-oauth-link-v3"/>Facebook-OAUTH-Link-v3 | アカウントリンク定義v3 | - | - | - | Facebook-OAUTH-Link-Base |
| Facebook-Unlink | [Deprecated]アカウントアンリンク定義v2。今後は[Facebook-Unlink-v3](./aadb2c_selmid_extension.md#idp_facebook-unlink-v3)を利用してください。 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimValueOnWhichToEnable</td><td>facebook.com</td></tr></table> | - | issuerToUnlink | SocialAccount-Unlink |
| <a id="idp_facebook-unlink-v3"/>Facebook-Unlink-v3 | アカウントアンリンク定義v3 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimValueOnWhichToEnable</td><td>facebook.com</td></tr></table> | - | issuerToUnlink | SocialAccount-Unlink-v3 |

### twitter接続定義（Domain：twitter.com）
| ID | 概要 | Metadata | 入力 | 出力 | IncludeTechnicalProfile |
|:---|:---|:---|:---|:---|:---|
| Twitter-OAUTH1-Base | 接続の共通定義 | - | - | issuerUserId<br>displayName<br>email<br>identityProvider<br>authenticationSource | - |
| Twitter-OAUTH1 | [Deprecated]接続定義v1。今後は[Twitter-OAUTH1-SignIn-v3](./aadb2c_selmid_extension.md#idp_twitter-oauth1-signin-v3)を利用してください。 | - | - | - | Twitter-OAUTH1-Base |
| Twitter-OAUTH1-SignIn | [Deprecated]接続定義v2。今後は[Twitter-OAUTH1-SignIn-v3](./aadb2c_selmid_extension.md#idp_twitter-oauth1-signin-v3)を利用してください。 | - | - | - | Twitter-OAUTH1-Base |
| <a id="idp_twitter-oauth1-signin-v3"/>Twitter-OAUTH1-SignIn-v3 | 接続定義v3 | - | - | - | Twitter-OAUTH1-Base |
| Twitter-OAUTH1-Link-Base | アカウントリンクの共通定義 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimTypeOnWhichToEnable</td><td>issuers</td></tr><tr><td>ClaimValueOnWhichToEnable</td><td>twitter.com</td></tr></table> | - | issuerUserIdToLink<br>issuerToLink | Twitter-OAUTH1-Base |
| Twitter-OAUTH1-Link | [Deprecated]アカウントリンク定義v2。今後は[Twitter-OAUTH1-Link-v3](./aadb2c_selmid_extension.md#idp_twitter-oauth1-link-v3)を利用してください。 | - | - | - | Twitter-OAUTH1-Link-Base |
| <a id="idp_idp_twitter-oauth1-link-v3"/>Twitter-OAUTH1-Link-v3 | アカウントリンク定義v3 | - | - | - | Twitter-OAUTH1-Link-Base |
| Twitter-Unlink | [Deprecated]アカウントアンリンク定義v2。今後は[Twitter-Unlink-v3](./aadb2c_selmid_extension.md#idp_twitter-unlink-v3)を利用してください。 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimValueOnWhichToEnable</td><td>twitter.com</td></tr></table> | - | issuerToUnlink | SocialAccount-Unlink |
| <a id="idp_twitter-unlink-v3"/>Twitter-Unlink-v3 | アカウントアンリンク定義v3 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimValueOnWhichToEnable</td><td>twitter.com</td></tr></table> | - | issuerToUnlink | SocialAccount-Unlink-v3 |

### Google接続定義（Domain：google.com）
| ID | 概要 | Metadata | 入力 | 出力 | IncludeTechnicalProfile |
|:---|:---|:---|:---|:---|:---|
| Google-OAUTH-Base | 接続の共通定義 | - | - | issuerUserId<br>displayName<br>email<br>givenName<br>surname<br>identityProvider<br>authenticationSource | - |
| Google-OAUTH | [Deprecated]接続定義v1。今後は[Google-OAUTH-SignIn-v3](./aadb2c_selmid_extension.md#idp_google-oauth-signin-v3)を利用してください。 | - | - | - | Google-OAUTH-Base |
| Google-OAUTH-SignIn | [Deprecated]接続定義v2。今後は[Google-OAUTH-SignIn-v3](./aadb2c_selmid_extension.md#idp_google-oauth-signin-v3)を利用してください。 | - | - | - | Google-OAUTH-Base |
| <a id="idp_google-oauth-signin-v3"/>Google-OAUTH-SignIn-v3 | 接続定義v3 | - | - | - | Google-OAUTH-Base |
| Google-OAUTH-Link-Base | アカウントリンクの共通定義 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimTypeOnWhichToEnable</td><td>issuers</td></tr><tr><td>ClaimValueOnWhichToEnable</td><td>google.com</td></tr></table> | - | issuerUserIdToLink<br>issuerToLink | Google-OAUTH-Base |
| Google-OAUTH-Link | [Deprecated]アカウントリンク定義v2。今後は[Google-OAUTH-Link-v3](./aadb2c_selmid_extension.md#idp_google-oauth-link-v3)を利用してください。 | - | - | - | Google-OAUTH-Link-Base |
| <a id="idp_google-oauth-link-v3"/>Google-OAUTH-Link-v3 | アカウントリンク定義v3 | - | - | - | Google-OAUTH-Link-Base |
| Google-Unlink | [Deprecated]アカウントアンリンク定義v2。今後は[Google-Unlink-v3](./aadb2c_selmid_extension.md#idp_google-unlink-v3)を利用してください。 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimValueOnWhichToEnable</td><td>google.com</td></tr></table> | - | issuerToUnlink | SocialAccount-Unlink |
| <a id="idp_google-unlink-v3"/>Google-Unlink-v3 | アカウントアンリンク定義v3 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimValueOnWhichToEnable</td><td>google.com</td></tr></table> | - | issuerToUnlink | SocialAccount-Unlink-v3 |

### LINE接続定義（Domain：line.me）
| ID | 概要 | Metadata | 入力 | 出力 | IncludeTechnicalProfile |
|:---|:---|:---|:---|:---|:---|
| LINE-OIDC-Base | 接続の共通定義 | - | - | issuerUserId<br>displayName<br>email<br>identityProvider<br>authenticationSource | - |
| LINE-OIDC | [Deprecated]接続定義v1。今後は[LINE-OIDC-SignIn-v3](./aadb2c_selmid_extension.md#idp_line-oidc-signin-v3)を利用してください。 | - | - | - | LINE-OIDC-Base |
| LINE-OIDC-SignIn | [Deprecated]接続定義v2。今後は[LINE-OIDC-SignIn-v3](./aadb2c_selmid_extension.md#idp_line-oidc-signin-v3)を利用してください。 | - | - | - | LINE-OIDC-Base |
| <a id="idp_line-oidc-signin-v3"/>LINE-OIDC-SignIn-v3 | 接続定義v3 | - | - | - | LINE-OIDC-Base |
| LINE-OIDC-Link-Base | アカウントリンクの共通定義 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimTypeOnWhichToEnable</td><td>issuers</td></tr><tr><td>ClaimValueOnWhichToEnable</td><td>line.me</td></tr></table> | - | issuerUserIdToLink<br>issuerToLink | LINE-OIDC-Base |
| LINE-OIDC-Link | [Deprecated]アカウントリンク定義v2。今後は[LINE-OIDC-Link-v3](./aadb2c_selmid_extension.md#idp_line-oidc-link-v3)を利用してください。 | - | - | - | LINE-OIDC-Link-Base |
| <a id="idp_line-oidc-link-v3"/>LINE-OIDC-Link-v3 | アカウントリンク定義v3 | - | - | - | LINE-OIDC-Link-Base |
| LINE-Unlink | [Deprecated]アカウントアンリンク定義v2。今後は[LINE-Unlink-v3](./aadb2c_selmid_extension.md#idp_line-unlink-v3)を利用してください。 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimValueOnWhichToEnable</td><td>line.me</td></tr></table> | - | issuerToUnlink | SocialAccount-Unlink |
| <a id="idp_line-unlink-v3"/>LINE-Unlink-v3 | アカウントアンリンク定義v3 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimValueOnWhichToEnable</td><td>line.me</td></tr></table> | - | issuerToUnlink | SocialAccount-Unlink-v3 |

### Yahoo! JAPAN接続定義（Domain：yahoo.co.jp）
| ID | 概要 | Metadata | 入力 | 出力 | IncludeTechnicalProfile |
|:---|:---|:---|:---|:---|:---|
| YahooJAPAN-OAUTH-Base | 接続の共通定義 | - | - | issuerUserId<br>displayName<br>email<br>givenName<br>surname<br>identityProvider<br>authenticationSource | - |
| YahooJAPAN-OAUTH | [Deprecated]接続定義v1。今後は[YahooJAPAN-OAUTH-SignIn-v3](./aadb2c_selmid_extension.md#idp_yahoojapan-oauth-signin-v3)を利用してください。 | - | - | - | YahooJAPAN-OAUTH-Base |
| YahooJAPAN-OAUTH-SignIn | [Deprecated]接続定義v2。今後は[YahooJAPAN-OAUTH-SignIn-v3](./aadb2c_selmid_extension.md#idp_yahoojapan-oauth-signin-v3)を利用してください。 | - | - | - | YahooJAPAN-OAUTH-Base |
| <a id="idp_yahoojapan-oauth-signin-v3"/>YahooJAPAN-OAUTH-SignIn-v3 | 接続定義v3 | - | - | - | YahooJAPAN-OAUTH-Base |
| YahooJAPAN-OAUTH-Link-Base | アカウントリンクの共通定義 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimTypeOnWhichToEnable</td><td>issuers</td></tr><tr><td>ClaimValueOnWhichToEnable</td><td>yahoo.co.jp</td></tr></table> | - | issuerUserIdToLink<br>issuerToLink | YahooJAPAN-OAUTH-Base |
| YahooJAPAN-OAUTH-Link | [Deprecated]アカウントリンク定義v2。今後は[YahooJAPAN-OAUTH-Link-v3](./aadb2c_selmid_extension.md#idp_yahoojapan-oauth-link-v3)を利用してください。 | - | - | - | YahooJAPAN-OAUTH-Link-Base |
| <a id="idp_yahoojapan-oauth-link-v3"/>YahooJAPAN-OAUTH-Link-v3 | アカウントリンク定義v3 | - | - | - | YahooJAPAN-OAUTH-Link-Base |
| YahooJAPAN-Unlink | [Deprecated]アカウントアンリンク定義v2。今後は[YahooJAPAN-Unlink-v3](./aadb2c_selmid_extension.md#idp_yahoojapan-unlink-v3)を利用してください。 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimValueOnWhichToEnable</td><td>yahoo.co.jp</td></tr></table> | - | issuerToUnlink | SocialAccount-Unlink |
| <a id="idp_yahoojapan-unlink-v3"/>YahooJAPAN-Unlink-v3 | アカウントアンリンク定義v3 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimValueOnWhichToEnable</td><td>yahoo.co.jp</td></tr></table> | - | issuerToUnlink | SocialAccount-Unlink-v3 |

### Apple ID接続定義（Domain：apple.com） 注：シークレットを定期的に更新する必要があります
| ID | 概要 | Metadata | 入力 | 出力 | IncludeTechnicalProfile |
|:---|:---|:---|:---|:---|:---|
| Apple-OIDC-Base | 接続の共通定義 | - | - | issuerUserId<br>displayName<br>email<br>identityProvider<br>authenticationSource | - |
| Apple-OIDC | [Deprecated]接続定義v1。今後は[Apple-OIDC-SignIn-v3](./aadb2c_selmid_extension.md#idp_apple-oidc-signin-v3)を利用してください。 | - | - | - | Apple-OIDC-Base |
| Apple-OIDC-SignIn | [Deprecated]接続定義v2。今後は[Apple-OIDC-SignIn-v3](./aadb2c_selmid_extension.md#idp_apple-oidc-signin-v3)を利用してください。 | - | - | - | Apple-OIDC-Base |
| <a id="idp_apple-oidc-signin-v3"/>Apple-OIDC-SignIn-v3 | 接続定義v3 | - | - | - | Apple-OIDC-Base |
| Apple-OIDC-Link-Base | アカウントリンクの共通定義 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimTypeOnWhichToEnable</td><td>issuers</td></tr><tr><td>ClaimValueOnWhichToEnable</td><td>apple.com</td></tr></table> | - | issuerUserIdToLink<br>issuerToLink | Apple-OIDC-Base |
| Apple-OIDC-Link | [Deprecated]アカウントリンク定義v2。今後は[Apple-OIDC-Link-v3](./aadb2c_selmid_extension.md#idp_apple-oidc-link-v3)を利用してください。 | - | - | - | Apple-OIDC-Link-Base |
| <a id="idp_apple-oidc-link-v3"/>Apple-OIDC-Link-v3 | アカウントリンク定義v3 | - | - | - | Apple-OIDC-Link-Base |
| Apple-Unlink | [Deprecated]アカウントアンリンク定義v2。今後は[Apple-Unlink-v3](./aadb2c_selmid_extension.md#idp_apple-unlink-v3)を利用してください。 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimValueOnWhichToEnable</td><td>apple.com</td></tr></table> | - | issuerToUnlink | SocialAccount-Unlink |
| <a id="idp_apple-unlink-v3"/>Apple-Unlink-v3 | アカウントアンリンク定義v3 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimValueOnWhichToEnable</td><td>apple.com</td></tr></table> | - | issuerToUnlink | SocialAccount-Unlink-v3 |

### dアカウント・コネクト接続定義（Domain：docomo.ne.jp）
| ID | 概要 | Metadata | 入力 | 出力 | IncludeTechnicalProfile |
|:---|:---|:---|:---|:---|:---|
| dConnect-OIDC-Base | 接続の共通定義 | - | - | issuerUserId<br>displayName<br>email<br>givenName<br>surname<br>identityProvider<br>authenticationSource | - |
| dConnect-OIDC | [Deprecated]接続定義v1。今後は[dConnect-OIDC-SignIn-v3](./aadb2c_selmid_extension.md#idp_dconnect-oidc-signin-v3)を利用してください。 | - | - | - | dConnect-OIDC-Base |
| dConnect-OIDC-SignIn | [Deprecated]接続定義v2。今後は[dConnect-OIDC-SignIn-v3](./aadb2c_selmid_extension.md#idp_dconnect-oidc-signin-v3)を利用してください。 | - | - | - | dConnect-OIDC-Base |
| <a id="idp_dconnect-oidc-signin-v3"/>dConnect-OIDC-SignIn-v3 | 接続定義v3 | - | - | - | dConnect-OIDC-Base |
| dConnect-OIDC-Link-Base | アカウントリンクの共通定義 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimTypeOnWhichToEnable</td><td>issuers</td></tr><tr><td>ClaimValueOnWhichToEnable</td><td>docomo.ne.jp</td></tr></table> | - | issuerUserIdToLink<br>issuerToLink | dConnect-OIDC-Base |
| dConnect-OIDC-Link | [Deprecated]アカウントリンク定義v2。今後は[dConnect-OIDC-Link-v3](./aadb2c_selmid_extension.md#idp_dconnect-oidc-link-v3)を利用してください。 | - | - | - | dConnect-OIDC-Link-Base |
| <a id="idp_dconnect-oidc-link-v3"/>dConnect-OIDC-Link-v3 | アカウントリンク定義v3 | - | - | - | dConnect-OIDC-Link-Base |
| dConnect-Unlink | [Deprecated]アカウントアンリンク定義v2。今後は[dConnect-Unlink-v3](./aadb2c_selmid_extension.md#idp_dconnect-unlink-v3)を利用してください。 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimValueOnWhichToEnable</td><td>docomo.ne.jp</td></tr></table> | - | issuerToUnlink | SocialAccount-Unlink |
| <a id="idp_dconnect-unlink-v3"/>dConnect-Unlink-v3 | アカウントアンリンク定義v3 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimValueOnWhichToEnable</td><td>docomo.ne.jp</td></tr></table> | - | issuerToUnlink | SocialAccount-Unlink-v3 |

### auID接続定義（Domain：kddi.com）
| ID | 概要 | Metadata | 入力 | 出力 | IncludeTechnicalProfile |
|:---|:---|:---|:---|:---|:---|
| auID-OIDC-Base | 接続の共通定義 | - | - | issuerUserId<br>displayName<br>email<br>identityProvider<br>authenticationSource | - |
| auID-OIDC | [Deprecated]接続定義v1。今後は[auID-OIDC-SignIn-v3](./aadb2c_selmid_extension.md#idp_auid-oidc-signin-v3)を利用してください。 | - | - | - | auID-OIDC-Base |
| auID-OIDC-SignIn | [Deprecated]接続定義v2。今後は[auID-OIDC-SignIn-v3](./aadb2c_selmid_extension.md#idp_auid-oidc-signin-v3)を利用してください。 | - | - | - | auID-OIDC-Base |
| <a id="idp_auid-oidc-signin-v3"/>auID-OIDC-SignIn-v3 | 接続定義v3 | - | - | - | auID-OIDC-Base |
| auID-OIDC-Link-Base | アカウントリンクの共通定義 | - | issuerUserIdToLink<br>issuerToLink | auID-OIDC-Base |
| auID-OIDC-Link | [Deprecated]アカウントリンク定義v2。今後は[auID-OIDC-Link-v3](./aadb2c_selmid_extension.md#idp_auid-oidc-link-v3)を利用してください。 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimTypeOnWhichToEnable</td><td>issuers</td></tr><tr><td>ClaimValueOnWhichToEnable</td><td>kddi.com</td></tr></table> | - | - | auID-OIDC-Link-Base |
| <a id="idp_auid-oidc-link-v3"/>auID-OIDC-Link-v3 | アカウントリンク定義v3 | - | - | - | auID-OIDC-Link-Base |
| auID-Unlink | [Deprecated]アカウントアンリンク定義v2。今後は[auID-Unlink-v3](./aadb2c_selmid_extension.md#idp_auid-unlink-v3)を利用してください。 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimValueOnWhichToEnable</td><td>kddi.com</td></tr></table> | - | issuerToUnlink | SocialAccount-Unlink |
| <a id="idp_auid-unlink-v3"/>auID-Unlink-v3 | アカウントアンリンク定義v3 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimValueOnWhichToEnable</td><td>kddi.com</td></tr></table> | - | issuerToUnlink | SocialAccount-Unlink-v3 |

## <a id="claimstransformation"></a>属性変換に関連する機能定義（`ClaimsProviders`エレメント配下）  
| ID | 概要 | Metadata | 入力 | 出力 | IncludeTechnicalProfile |
|:---|:---|:---|:---|:---|:---|
| SocialAccount-Unlink-Base | アカウントアンリンクの共通定義 | <table><tr><th>key</th><th>value</th></tr><tr><td>ClaimTypeOnWhichToEnable</td><td>issuers</td></tr></table> | - | issuerToUnlink | - |
| SocialAccount-Unlink | アカウントリンク定義v2。今後は[SocialAccount-Unlink-v3](./aadb2c_selmid_extension.md#socialaccount-unlink-v3)を利用してください。 | - | - | RemoveUserIdentityFromCollectionByIssuer | SocialAccount-Unlink-Base |
| <a id="socialaccount-unlink-v3"/>SocialAccount-Unlink-v3 | アカウントリンク定義v3 | - | - | RemoveAlternativeSecurityFromCollectionByIssuer | SocialAccount-Unlink-Base |
| GetContextData | コンテキスト情報を取得します | <table><tr><th>key</th><th>value</th></tr><tr><td>IncludeClaimResolvingInClaimsHandling</td><td>true</td></tr></table> | ipaddress<br>Culture<br>LanguageName<br>lang_ja<br>lang_en | - |
| AssertReadOnlyEmailNotChange | 二段階認証用画面（メールアドレス）でメールアドレスが画面で変更されていないかチェックします | - | - | readOnlyEmail | - |
| GenerateWelcomeMessage | Welcome用メールの本文を生成します | - | email | sendGridReqBody | - |
| GeneratePasswordChangeMessage | パスワード変更用メールの本文を生成します | - | email | sendGridReqBody | - |

## <a id="restapi"></a>REST APIに関連する機能定義（`ClaimsProviders`エレメント配下）  
| ID | 概要 | 入力 | 出力 | IncludeTechnicalProfile |
|:---|:---|:---|:---|:---|
| API-LINEFriendStatus | LINE公式アカウントの友だち関係を取得します | identityProviderAccessToken | extension_LINEFriend | - |
| REST-API-EVALUATE-CAPYDATA-FOR-RISKBASES | リスクベース認証用データの評価を行います | capy_userId<br>capy_data<br>capy_private_key<br>capy_riskbase_key | capy_risk_result<br>capy_risk_level<br>capy_risk_reasons<br>userMessage | - |
| REST-API-APPROVE-CAPYDATA-FOR-RISKBASES | リスクベース認証用データの承認を行います | capy_data<br>capy_private_key<br>capy_riskbase_key | capy_risk_result<br>capy_risk_reason<br>userMessage | - |
| REST-API-EVALUATE-CAPYDATA-FOR-PUZZLE | パズルキャプチャ用データの評価を行います | submit.capy_answer<br>submit.capy_challengekey<br>capy_private_key | capy_puzzle_result<br>capy_puzzle_reason<br>userMessage | - |
| REST-API-EVALUATE-CAPYBLACKLIST | リアルタイムブラックリストの評価を行います | capy_private_key<br>capy_blacklist_key | capy_black_types<br>capy_black_result<br>capy_black_value | - |
| REST-API-DISPLAY-FOR-USERMESSAGE | userMessageの表示を行います | - | - | - |
| REST-API-CUSTOMERINFO-MATCH | 本人確認（マッチング）を行います | - | status<br>userMessage<br>selmid_result<br>selmid_docomo_result_code<br>selmid_kddi_status<br>selmid_kddi_result_code<br>selmid_docomo_mb_result<br>selmid_docomo_mb_guidancecode<br>selmid_docomo_httpCode<br>selmid_docomo_httpMessage<br>selmid_docomo_moreInformation<br>selmid_kddi_error_result_code<br>selmid_kddi_error_message | - |
| SendGrid | SendGrid送信を行います | sendGridReqBody | - | - |
| SendOtp | [Deprecated]OTP用メール送信を行います。今後は[SendGeneralOtp](./aadb2c_selmid_extension.md#sendgeneralotp)を利用してください。 | - | - | SendGrid |
| <a id="sendgeneralotp"/>SendGeneralOtp | OTP用メール送信を行います | - | - | SendGrid |
| SendMfaOtp | MFA OTP用メール送信を行います | - | - | SendGrid |
| SendWelcomeMessage | Welcome用メール送信を行います | - | - | SendGrid |
| SendPasswordChangeMessage | パスワード変更用メール送信を行います | - | - | SendGrid |
| REST-API-TOTP-GENERATE | TOTPの認証コード生成を行います | - | selmid_totp_otpauth_url<br>selmid_totp_secret_code<br>extension_selmid_totp_secret_key | - |
| REST-API-TOTP-VERIFY | TOTPの認証コード生成を行います | selmid_totp_code<br>extension_selmid_totp_secret_key<br>extension_selmid_totp_timestepmatched | extension_selmid_totp_timestepmatched<br>selmid_result<br>userMessage | - |

## ローカルアカウントに関連する機能定義（`ClaimsProviders`エレメント配下）
| ID | 動作概要 | Metadata | 入力 | 出力 | 検証プロファイル |
|:---|:---|:---|:---|:---|:---|
| login-NonInteractive | ローカルアカウントのサインイン(Password Grant) | <table><tr><th>key</th><th>value</th></tr><tr><td>client_id</td><td></td></tr><tr><td>IdTokenAudience</td><td></td></tr></table> | client_id<br>resource_id | - | - |

## Azure Actvie Directoryに関連する機能定義（`ClaimsProviders`エレメント配下）
| ID | 動作概要 | Metadata | 入力 | 永続 | 出力 | IncludeTechnicalProfile |
|:---|:---|:---|:---|:---|:---|:---|
| AAD-Common | Active Directoryの共通プロファイル | <table><tr><th>key</th><th>value</th></tr><tr><td>ApplicationObjectId</td><td></td></tr><tr><td>ClientId</td><td></td></tr></table> | - | - | - | - |
| AAD-UserReadUsingUserIdentityToLink-NoError | [Deprecated]ディレクトリ内のソーシャル アカウントを検索します（アカウントリンク用）（存在しない場合でもエラーは発生しません）。今後は[AAD-UserReadUsingAlternativeSecurityIdToLink-NoError](./aadb2c_b2c_base.md#aaduserreadusingalternativesecurityidtolinknoerror)を利用してください。 | - | userIdentitiesToLink | - | objectIdToLink | AAD-Common |
| AAD-UserReadUsingUserIdentity | [Deprecated]ディレクトリ内のソーシャル アカウントを検索します（アカウントリンク用）。今後は[AAD-UserReadUsingAlternativeSecurityId](./aadb2c_b2c_base.md#aaduserreadusingalternativesecurityid)を利用してください。 | - | userIdentities | - | objectId<br>userIdentities | AAD-Common |
| AAD-UserReadUsingUserIdentity-NoError | [Deprecated]ディレクトリ内のソーシャル アカウントを検索します（アカウントリンク用）（存在しない場合のエラーなし）。今後は[AAD-UserReadUsingAlternativeSecurityId-NoError](./aadb2c_b2c_base.md#aaduserreadusingalternativesecurityidnoerror)を利用してください。 | - | - | - | - | AAD-UserReadUsingUserIdentity |
| AAD-UserWriteUsingUserIdentity | [Deprecated]userIdentitiesをキーに属性情報をAzure Active Directoryのデータベースへ登録します（アカウントリンク用） | - | userIdentities | userIdentities<br>userPrincipalName<br>mailNickName<br>displayName | objectId<br>userIdentities<br>newUser<br>otherMails | AAD-Common |
| AAD-UserUpdateWithUserIdentities | [Deprecated]アカウントリンク・アンリンク後の状態を更新します（アカウントリンク用）。今後は[AAD-AAD-UserUpdateWithAlternativeSecurityIds](./aadb2c_b2c_base.md#aaduserupdatewithalternativesecurityids)を利用してください。 | - | objectId | objectId<br>userIdentities | objectId<br>userIdentities | AAD-Common |
| Update-TOU-Status | 規約への同意状態を書き込みます | - | objectId | objectId<br>extension_termsOfUseConsentDateTime<br>extension_termsOfUseConsentVersion | extension_termsOfUseConsentDateTime<br>extension_termsOfUseConsentVersion | AAD-Common |
| Check-TOU-Status-by-Version | 規約への同意状態取得します（バージョンで比較する場合） | - | objectId | - | extension_termsOfUseConsentVersion<br>extension_termsOfUseConsentDateTime | AAD-Common |
| Check-TOU-Status-by-DateTime | 規約への同意状態取得します（日付で比較する場合） | - | objectId | - | extension_termsOfUseConsentVersion<br>extension_termsOfUseConsentDateTime | AAD-Common |

##  Application Insightsに関連する機能定義（`ClaimsProviders`エレメント配下）
| ID | 動作概要 | Metadata | 入力 |
|:---|:---|:---|:---|
| AzureInsights-Common | Active Directoryの共通プロファイル | <table><tr><th>key</th><th>value</th></tr><tr><td>InstrumentationKey</td><td></td></tr><tr><td>DeveloperMode</td><td>true</td></tr><tr><td>DisableTelemetry</td><td>false</td></tr></table> | <table><tr><th>ClaimTypeReferenceId</th><th>PartnerClaimType</th><th>DefaultValue</th></tr><tr><td>PolicyId</td><td>{property:Policy}</td><td>{Policy:PolicyId}</td></tr><tr><td>CorrelationId</td><td>{property:CorrelationId}</td><td>{Context:CorrelationId}</td></tr><tr><td>Culture</td><td>{property:Culture}</td><td>{Culture:RFC5646}</td></tr><tr><td>AppId</td><td>{property:App}</td><td>{OIDC:ClientId}</td></tr></table> |

## セルフ アサートに関連する機能定義（`ClaimsProviders`エレメント配下）
| ID | 動作概要 | 入力 | 出力 | 検証プロファイル |
|:---|:---|:---|:---|:---|
| SelfAsserted-Input-ToU-SignIn | 利用規約の表示、同意の取得のための画面 | objectId<br>termsOfUseConsentChoice | termsOfUseConsentChoice<br>extension_termsOfUseConsentVersion | Update-TOU-Status |
| MakeCapydata-ForRiskBases | リスクベース認証 Capyデータ作成画面 | capy_userId | capy_userId<br>capy_data | - |
| EmailVerifyOnSignIn | メールアドレス検証画面 | readOnlyEmail | readOnlyEmail | - |
| SelfAsserted-Error | エラーメッセージ画面 | errorMessage | errorMessage | - |
| SelfAsserted-Social-v2 | [Deprecated]ソーシャルアカウントのサインアップ画面。今後は[AAD-AAD-UserUpdateWithAlternativeSecurityIds](./aadb2c_b2c_base.md#selfassertedsocial)を利用してください。 | displayName<br>givenName<br>surname | displayName<br>givenName<br>surname | AAD-UserWriteUsingUserIdentity |
| AppFactor-TOTP-Regist | TOTP登録画面(QR表示&コード検証) | selmid_totp_secret_code<br>selmid_totp_otpauth_url<br>extension_selmid_totp_secret_key | selmid_totp_code<br>selmid_totp_secret_code<br>selmid_totp_otpauth_url<br>extension_selmid_totp_timestepmatched | - |
| AppFactor-TOTP-Verify | TOTP検証画面(コード検証) | extension_selmid_totp_secret_key<br>extension_selmid_totp_timestepmatched | selmid_totp_code<br>extension_selmid_totp_timestepmatched | - |

## OneTimePasswordに関連する機能定義（`ClaimsProviders`エレメント配下）
| ID | 動作概要 | Metadata | 入力 | 出力 | IncludeTechnicalProfile |
|:---|:---|:---|:---|:---|:---|
| GenerateOtp-Common | ワンタイムパスワード生成の共通定義 | <table><tr><th>key</th><th>value</th></tr><tr><td>Operation</td><td>GenerateCode</td></tr><tr><td>CodeExpirationInSeconds</td><td>1200</td></tr><tr><td>CodeLength</td><td>6</td></tr><tr><td>CharacterSet</td><td>a-zA-Z0-9</td></tr><tr><td>ReuseSameCode</td><td>true</td></tr><tr><td>MaxNumAttempts</td><td>5</td></tr></table> | - | - | - |
| VerifyOtp-Common | ワンタイムパスワード検証の共通定義 | <table><tr><th>key</th><th>value</th></tr><tr><td>Operation</td><td>VerifyCode</td></tr><tr><td>UserMessage.VerificationHasExpired</td><td>You have exceed the maximum time allowed.</td></tr><tr><td>UserMessage.MaxRetryAttemped</td><td>You have exceed the number of retries allowed.</td></tr><tr><td>UserMessage.InvalidCode</td><td>You have entered the wrong code.</td></tr><tr><td>UserMessage.ServerError</td><td>Cannot verify the code, please try again later.</td></tr></table>
 | - | - | - |
| GenerateOtp | [Deprecated]ワンタイムパスワードを生成します。今後は[GenerateGeneralOtp](./aadb2c_selmid_extension.md#generategeneralotp)を利用してください。 | - | email | otp | GenerateOtp-Common |
| VerifyOtp | [Deprecated]ワンタイムパスワードを検証します。今後は[VerifyGeneralOtp](./aadb2c_selmid_extension.md#verifygeneralotp)を利用してください。 | - | email<br>verificationCode | - | VerifyOtp-Common |
| <a id="generategeneralotp"/>GenerateGeneralOtp | ワンタイムパスワードを生成します。 | - | - | otp | GenerateOtp-Common |
| <a id="verifygeneralotp"/>VerifyGeneralOtp | ワンタイムパスワードを検証します。 | - | verificationCode | - | VerifyOtp-Common |
| GenerateMfaOtp | MFA用ワンタイムパスワードを生成します。 | - | - | otp | GenerateOtp-Common |
| VerifyMfaOtp | MFA用ワンタイムパスワードを検証します。 | - | verificationCode | - | VerifyOtp-Common |

## RelyingPartyに関連する機能定義（`RelyingParty`エレメント配下）
### UserJourneyBehaviors
| 要素 | 属性 | 値 |
|:---|:---|:---|
| JourneyInsights | TelemetryEngine | ApplicationInsights |
| - | InstrumentationKey |  |
| - | DeveloperMode | false |
| - | ClientEnabled | true |
| - | ServerEnabled | true |
| - | TelemetryVersion | 1.0.0 |
| - | TelemetryEngine | ApplicationInsights |
