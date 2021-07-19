# B2C_BASE_V4
 - Azure AD B2Cで標準で用意されている または 標準的な機能に関する各定義を行うファイル。
 - バージョン：4

## <a id="claimtype"></a> ClaimType定義(`ClaimsSchema`エレメント配下)
| ID | 概要 |
|:---|:---|
| issuerUserId | 発行者のユーザID |
| tenantId | テナントID |
| signInName | サインイン名 |
| email | メールアドレス |
| newPassword | 新しいパスワード |
| reenterPassword | 確認用パスワード |
| Verified.strongAuthenticationPhoneNumber | 確認済みの電話番号 |
| readOnlyEmail | 読み取り用メールアドレス |
| upnUserName | ユーザー プリンシパル名 (UPN) |
| sub | OpenId ConnectのSubject |
| identityProvider | 外部IdPの識別子 |
| authenticationSource | 認証元（ローカル、外部IdP） |
| newUser | 新規作成されたユーザかを示す |
| executed-SelfAsserted-Input | 属性がユーザーから収集されたかどうかを示す |
| objectIdFromSession | オブジェクトIDがSSOセッションから取得されたことを示す |
| isActiveMFASession | ユーザーがアクティブなMFAセッションを持っていることを示す |
| newPhoneNumberEntered | 新しい電話番号が有効かを示す |
| EventType | ユーザー動作の追跡用 |
| PolicyId | 要求リゾルバーのPolicy:PolicyId |
| Culture | 要求リゾルバーのCulture:RFC5646 |
| LanguageName | 要求リゾルバーのCulture:LanguageName |
| CorrelationId | 要求リゾルバーのContext:CorrelationId |
| AppId | ユーザー動作の追跡用の項目 |
| federatedUser | ユーザー動作の追跡用の項目 |
| parsedDomain | ユーザー動作の追跡用の項目 |
| userInLocalDirectory | ユーザー動作の追跡用の項目 |
| issuerUserIdToLink | アカウントリンク用の発行者のユーザID |
| issuerToLink | アカウントリンク用の外部IdPの識別子 |
| <a id="alternativesecurityidtolink"/>alternativeSecurityIdToLink | アカウントリンク用のalternativeSecurityId |
| objectIdToLink | alternativeSecurityIdToLinkをもとに取得したobjectId |
| issuerToUnlink | アカウントリンク用の外部IdPの識別子（削除用） |
| extractTargetAlternativeSecurityIds | アカウントリンク用のalternativeSecurityIds |
| issuers | extractTargetAlternativeSecurityIdsの外部IdPの識別子を格納 |
| client_id | 認証リクエストパラメータ |
| resource_id | 認証リクエストパラメータ |
| nca | 認証リクエストパラメータ |
| grant_type | 認証リクエストパラメータ |
| scope | 認証リクエストパラメータ |
| accountEnabled | Azure ADユーザープロファイルの属性 [公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/user-profile-attributes) |
| <a id="alternativesecurityid"/>alternativeSecurityId | Azure ADユーザープロファイルの属性 [公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/user-profile-attributes) |
| <a id="alternativesecurityids"/>alternativeSecurityIds | Azure ADユーザープロファイルの属性 [公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/user-profile-attributes) |
| displayName | Azure ADユーザープロファイルの属性 [公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/user-profile-attributes) |
| givenName | Azure ADユーザープロファイルの属性 [公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/user-profile-attributes) |
| surname | Azure ADユーザープロファイルの属性 [公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/user-profile-attributes) |
| mailNickName | Azure ADユーザープロファイルの属性 [公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/user-profile-attributes) |
| objectId | Azure ADユーザープロファイルの属性 [公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/user-profile-attributes) |
| otherMails | Azure ADユーザープロファイルの属性 [公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/user-profile-attributes) |
| password | Azure ADユーザープロファイルの属性 [公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/user-profile-attributes) |
| passwordPolicies | Azure ADユーザープロファイルの属性 [公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/user-profile-attributes) |
| signInNames.emailAddress | Azure ADユーザープロファイルの属性 [公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/user-profile-attributes) |
| strongAuthenticationPhoneNumber | Azure ADユーザープロファイルの属性 [公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/user-profile-attributes) |
| refreshTokensValidFromDateTime | Azure ADユーザープロファイルの属性 [公式ドキュメント](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/user-profile-attributes) |

## <a id="claimstransformations"></a>属性変換ルール定義（`ClaimsTransformations`エレメント配下）
| ID | 動作概要 | 入力 | 出力 |
|:---|:---|:---|:---|
| CreateOtherMailsFromEmail | メールアドレスをotherMailsコレクションに加えます | email | otherMails |
| CreateRandomUPNUserName | GUID形式でupnUserNameを生成します | - | upnUserName |
| CreateUserPrincipalName | cpim_{upnUserName}@{tenant名}形式でuserPrincipalName（Azure AD B2C内部の識別子）を生成します<br>例）cpim_32407727-a73a-4944-9fdb-54cf4d755ddf@yourtenant.onmicrosoft.com | upnUserName | userPrincipalName |
| <a id="createalternativesecurityid"/>CreateAlternativeSecurityId | 外部IdPの識別子からalternativeSecurityIdを生成します | issuerUserId<br>identityProvider | alternativeSecurityId |
| <a id="createalternativesecurityidtolink"/>CreateAlternativeSecurityIdToLink | 外部IdPの識別子からalternativeSecurityIdを生成します | issuerUserId<br>identityProvider | alternativeSecurityId |
| <a id="appendalternativesecurityid"/>AppendAlternativeSecurityId | alternativeSecurityIdをalternativeSecurityIdsに加えます | alternativeSecurityId<br>alternativeSecurityIds | alternativeSecurityIds |
| <a id="appendalternativesecurityidtolink"/>AppendAlternativeSecurityIdToLink | alternativeSecurityIdToLinkをalternativeSecurityIdsに加えます | alternativeSecurityIdToLink<br>alternativeSecurityIds | alternativeSecurityIds |
| <a id="removealternativesecurityfromcollectionbyissuer"/>RemoveAlternativeSecurityFromCollectionByIssuer | issuerToUnlinkをalternativeSecurityIds 要求から削除します | issuerToUnlink<br>alternativeSecurityIds | alternativeSecurityIds |
| <a id="extractissuersfromextracttargetalternativesecurityids"/>ExtractIssuersFromExtractTargetAlternativeSecurityIds | 外部IdPの識別子の一覧を extractTargetAlternativeSecurityIdsからissuersに返します | extractTargetAlternativeSecurityIds | issuers |
| AssertAccountEnabledIsTrue | accountEnabled属性がtrueならtrueを返却します | accountEnabled | True/False |
| CreateUserIdForMFA | 多要素認証用のuserId属性を生成します<br>{objectId}@{tenant名}の形式 | objectId | userIdForMFA |
| CopyEmailToReadOnly | email属性の値をreadOnlyEmail属性にコピーします | email | readOnlyEmail |

## UI定義（`ContentDefinitions`エレメント配下）
| ID | 概要 | DataUri |
|:---|:---|:---|
| api.error | エラー ページ - 例外またはエラーが発生したときにエラーページを表示します。 | urn:com:microsoft:aad:b2c:elements:contract:globalexception:1.2.1 |
| api.idpselections | ID プロバイダーの選択ページ - ユーザーがサインイン時に選択できる ID プロバイダーを一覧表示します。 ID プロバイダーは、通常、エンタープライズ ID プロバイダー、ソーシャル ID プロバイダー (Facebook や Google+ など)、ローカル アカウントのいずれかです。 | urn:com:microsoft:aad:b2c:elements:contract:providerselection:1.2.1 |
| api.idpselections.signup | サインアップのための ID プロバイダーの選択 - ユーザーがサインアップ時に選択できる ID プロバイダーを一覧表示します。 ID プロバイダーは、通常、エンタープライズ ID プロバイダー、ソーシャル ID プロバイダー (Facebook や Google+ など)、ローカル アカウントのいずれかです。 | urn:com:microsoft:aad:b2c:elements:contract:providerselection:1.2.1 |
| api.signuporsignin | 統合されたサインアップ ページまたはサインイン ページ - ユーザーのサインアップおよびサインイン プロセスを処理します。 ユーザーは、エンタープライズ ID プロバイダー、ソーシャル ID プロバイダー (Facebook や Google+ など)、ローカル アカウントのいずれかを使用できます。 | urn:com:microsoft:aad:b2c:elements:contract:unifiedssp:2.1.4 |
| api.selfasserted | ソーシャル アカウントのサインアップ ページ - ソーシャル ID プロバイダーの既存のアカウントを使用してサインアップするときに、ユーザーが入力する必要があるフォームを表示します。 このページは、パスワード入力フィールドを除いて、上記のソーシャル アカウントのサインアップ ページに似ています。 | urn:com:microsoft:aad:b2c:elements:contract:selfasserted:2.1.4 |
| api.selfasserted.profileupdate | プロファイルの更新ページ - ユーザーがプロファイルを更新するためにアクセスできるフォームを表示します。 このページは、パスワード入力フィールドを除いて、ソーシャル アカウントのサインアップ ページに似ています。 | urn:com:microsoft:aad:b2c:elements:contract:selfasserted:2.1.4 |
| api.localaccountsignup | ローカル アカウントのサインアップ ページ - 電子メール アドレスまたはユーザー名に基づいたローカル アカウントでサインアップするためのフォームを表示します。 このフォームには、テキスト入力ボックス、パスワード入力ボックス、ラジオ ボタン、単一選択ドロップダウン ボックス、複数選択チェック ボックスなど、さまざまな入力コントロールを含めることができます。 | urn:com:microsoft:aad:b2c:elements:contract:selfasserted:2.1.4 |
| api.localaccountpasswordreset | パスワードを忘れた場合のページ - パスワードのリセットを開始するためにユーザーが入力する必要があるフォームを表示します。 | urn:com:microsoft:aad:b2c:elements:contract:selfasserted:2.1.4 |
| api.phonefactor | 多要素認証ページ - サインアップ中またはサインイン中にテキストまたは音声を使用して電話番号を確認します。 | urn:com:microsoft:aad:b2c:elements:contract:multifactor:1.2.4 |
| api.signuporsigninwithkmsi | サインインしたまま機能付き 統合されたサインアップ ページまたはサインイン ページ - ユーザーのサインアップおよびサインイン プロセスを処理します。 ユーザーは、エンタープライズ ID プロバイダー、ソーシャル ID プロバイダー (Facebook や Google+ など)、ローカル アカウントのいずれかを使用できます。（api.signuporsigninを利用してください（setting.enableRememberMe属性で指定可能です）） | urn:com:microsoft:aad:b2c:elements:contract:unifiedssp:2.1.4 |

## Azure Actvie Directoryに関連する機能定義（`ClaimsProviders`エレメント配下）
| ID | 動作概要 | 入力 | 永続 | 出力 | IncludeTechnicalProfile |
|:---|:---|:---|:---|:---|:---|
| AAD-Common | Active Directoryの共通プロファイル | - | - | - | - |
| AAD-UserWriteUsingAlternativeSecurityId | 新しいソーシャル アカウントを作成します | alternativeSecurityId | alternativeSecurityId<br>userPrincipalName<br>mailNickName<br>displayName| objectId<br>newUser | AAD-Common |
| <a id="aaduserreadusingalternativesecurityid"/>AAD-UserReadUsingAlternativeSecurityId | ディレクトリ内のソーシャル アカウントを検索します | alternativeSecurityId | - | objectId | AAD-Common |
| <a id="aaduserreadusingalternativesecurityidnoerror"/>AAD-UserReadUsingAlternativeSecurityId-NoError | ディレクトリ内のソーシャル アカウントを検索します（存在しない場合でもエラーは発生しません） | alternativeSecurityId | - | objectId | AAD-Common |
| AAD-UserWriteUsingLogonEmail | 新しいローカル アカウントを作成します | email | email<br>newPassword<br>passwordPolicies| objectId<br>authenticationSource<br>userPrincipalName<br>signInNames.emailAddress | AAD-Common |
| AAD-UserReadUsingEmailAddress | ディレクトリ内のローカル アカウントを検索します | email | - | objectId<br>authenticationSource<br>userPrincipalName<br>displayName<br>accountEnabled<br>otherMails<br>signInNames.emailAddress | AAD-Common |
| AAD-UserWriteUsingLogonEmail | 新しいローカル アカウントを作成します | email | email<br>newPassword<br>passwordPolicies| objectId<br>authenticationSource<br>userPrincipalName<br>signInNames.emailAddress | AAD-Common |
| AAD-UserWritePasswordUsingObjectId | ローカル アカウントのパスワードを更新します | objectId | objectId<br>newPassword | - | AAD-Common |
| AAD-UserWriteProfileUsingObjectId | ユーザープロファイルを更新します | objectId | objectId | - | AAD-Common |
| AAD-UserReadUsingObjectId | ユーザープロファイルを読み取ります | objectId | - | - | AAD-Common |
| AAD-DeleteClaimsUsingObjectId | 指定された属性をユーザープロファイルから消去します | objectId | objectId | - | AAD-Common |
| AAD-DeleteUserUsingObjectId | ユーザーアカウントを削除します | objectId | - | - | AAD-Common |
| <a id="aaduserreadusingalternativesecurityidtolinknoerror"/>AAD-UserReadUsingAlternativeSecurityIdToLink-NoError | ディレクトリ内のソーシャル アカウントを検索します（アカウントリンク用）（存在しない場合でもエラーは発生しません） | alternativeSecurityIdToLink | - | objectIdToLink | AAD-Common |
| <a id="aaduserupdatewithalternativesecurityids"/>AAD-UserUpdateWithAlternativeSecurityIds | アカウントリンク・アンリンク後の状態を更新します（アカウントリンク用） | objectId | objectId<br>alternativeSecurityIds | objectId<br>alternativeSecurityIds<br>extractTargetAlternativeSecurityIds | AAD-Common |

## セルフ アサートに関連する機能定義（`ClaimsProviders`エレメント配下）
| ID | 動作概要 | 入力 | 出力 | 検証プロファイル |
|:---|:---|:---|:---|:---|
| <a id="selfassertedsocial"/>SelfAsserted-Social | ソーシャルアカウントのサインアップ画面 | - | objectId<br>newUser<br>executed-SelfAsserted-Input | AAD-UserWriteUsingAlternativeSecurityId |
| SelfAsserted-ProfileUpdate | プロファイルの編集画面 | alternativeSecurityId<br>userPrincipalName | executed-SelfAsserted-Input | AAD-UserWriteProfileUsingObjectId | 

## ローカルアカウントに関連する機能定義（`ClaimsProviders`エレメント配下）
| ID | 動作概要 | 入力 | 出力 | 検証プロファイル |
|:---|:---|:---|:---|:---|
| login-NonInteractive | ローカルアカウントのサインイン(Password Grant) | signInName<br>password<br>grant_type<br>scope<br>nca | objectId<br>tenantId<br>userPrincipalName <br>authenticationSource| - |
| LocalAccountSignUpWithLogonEmail | ローカルアカウント（email）のサインアップ画面 | email | objectId<br>email<br>newPassword<br>reenterPassword<br>newUser<br>executed-SelfAsserted-Input<br>authenticationSource | AAD-UserWriteUsingLogonEmail |
| LocalAccountDiscoveryUsingEmailAddress | 画面で入力されたメールアドレスを検証後、ディレクトリ内のローカル アカウントをメールアドレスをキーに検索します | - | email<br>objectId<br>userPrincipalName<br>authenticationSource | AAD-UserReadUsingEmailAddress |
| LocalAccountWritePasswordUsingObjectId | 画面で入力されたパスワードでローカル アカウントのパスワードを更新します | objectId | newPassword<br>reenterPassword | AAD-UserWritePasswordUsingObjectId |

## PhoneFactorに関連する機能定義（`ClaimsProviders`エレメント配下）
| ID | 動作概要 | 入力変換 | 入力 | 出力 |
|:---|:---|:---|:---|:---|
| PhoneFactor-InputOrVerify | 電話番号を検証または登録するための画面 | CreateUserIdForMFA | userIdForMFA<br>strongAuthenticationPhoneNumber | Verified.strongAuthenticationPhoneNumber<br>newPhoneNumberEntered |

## セッション管理定義（`ClaimsProviders`エレメント配下）
| ID | 概要 | 永続 | 出力 | IncludeTechnicalProfile |
|:---|:---|:---|:---|:---|
| SM-Noop | このプロバイダーは何もしません。 特定の技術プロファイルの SSO 動作を抑制するために使用できます。| - | - | - |
| SM-AAD | ローカルアカウントのサインアップ・サインインセッションを管理します| objectId<br>signInName<br>authenticationSource<br>identityProvider<br>newUser<br>executed-SelfAsserted-Input | objectIdFromSession | - |
| SM-SocialSignup | ソーシャルアカウントのサインアップセッションを管理します| SM-AADと同様 | - | - |
| SM-SocialLogin | ソーシャルアカウントのサインインセッションを管理します| alternativeSecurityId | - | SM-AAD |
| SM-MFA | 多要素認証セッションを管理します| Verified.strongAuthenticationPhoneNumber | - | - |
| SM-jwt-issuer | OAuth2 または OpenId Connect と Azure AD B2C 間のセッションを管理します| - | - | - |
| SM-Saml-idp | SAML IDP と Azure AD B2C 間のセッションを管理します| - | - | - |
| SM-Saml-issuer | SAML SP と Azure AD B2C 間のセッションを管理します| - | - | - |

## トークン発行者定義（`ClaimsProviders`エレメント配下）
| ID | 概要 |
|:---|:---|
| JwtIssuer | アプリケーションに返却される JWT トークンを発行します |
| [Saml2AssertionIssuer](#saml2assertionissuer) | アプリケーション (サービス プロバイダー) に返される SAML トークンを出力します |


### Saml2AssertionIssuer
利用に当たって次の設定を行う必要があります。
#### SAML entityID のカスタマイズ
Metadataの`IssuerUri`値で指定します。

#### 暗号化キーの指定
CryptographicKeysで指定します。
| ID | 説明 |
|:---|:---|
| SamlMessageSigning | SAML メッセージを署名するために使用する X509 証明書 (RSA キー セット)。 Azure AD B2C では、このキーを使用して、要求に署名し、ID プロバイダーに送信します。|
| SamlAssertionSigning |X509 証明書 (RSA キー セット)。 SAML ID プロバイダーは、証明書の公開部分を使用して、SAML 応答のアサーションを暗号化します。 Azure AD B2C は、証明書の非公開部分を使用してアサーションの暗号化を解除します。 |
| SamlAssertionDecryption | SAML データを署名するために使用する X509 証明書 (RSA キー セット)。 Azure AD B2C では、このキーを使用して、メタデータに署名します。 |

#### 例）
```
<Metadata>
  <!-- Azure AD B2C からのSAML応答で返される発行者のURIを指定 -->
  <Item Key="IssuerUri">https://yourtenant.b2clogin.com/yourtenant.onmicrosoft.com/B2C_1A_B2C_BASE</Item>
</Metadata>
<CryptographicKeys>
  <!-- 暗号化キーの情報 署名を行う際に使用するX509証明書を指定 -->
  <Key Id="SamlMessageSigning" StorageReferenceId="B2C_1A_SamlIdpCert" />
  <Key Id="SamlAssertionSigning" StorageReferenceId="B2C_1A_SamlIdpCert" />
  <Key Id="SamlAssertionDecryption" StorageReferenceId="B2C_1A_SamlIdpCert" />
</CryptographicKeys>
```

## Application Insights定義（`ClaimsProviders`エレメント配下）
[ユーザー動作の追跡](https://docs.microsoft.com/ja-jp/azure/active-directory-b2c/analytics-with-application-insights)で利用するイベント定義。
必要に応じてイベントの追加や属性の追加を[USER_EXTENSION_BASE](./aadb2c_config.md#user_extension_base)にて定義してください。

| ID | 概要 | イベント名 | 属性 | IncludeTechnicalProfile |
|:---|:---|:---|:---|:---|
| AzureInsights-Common | AzureInsightsの共通プロファイル | - | - | - |
| AzureInsights-SignInRequest | サインインリクエスト時 | SignInRequest | - | AzureInsights-Common |
| AzureInsights-UserSignup | サインインアップ時 | UserSignup | - | AzureInsights-Common |
| AzureInsights-SignInComplete | サインイン（サインアップ）完了時 | SignInComplete | federatedUser<br>parsedDomain<br>identityProvider<br>displayName | AzureInsights-Common |
