# SELMID 各ブリッジAPI
 - IEFで用意されているTechnicalProfile等で対応出来ない処理を外部のAPIと連携することで実現することができます
 - カスタムポリシーからのAPI呼び出しを行い処理を行います

## <a id="list"></a> API一覧
| 分類 | 機能 | エンドポイント |  概要 |
|:---|:---|:---|:---|
| 共通処理 | userMessage表示処理 | DisplayForUserMessage | SelfAssertedAttributeProviderのバリデーション処理で画面上に表示するメッセージを返します |
| Capy処理 | リスクベース認証評価処理 | CapyRiskbasesEvaluate | capy_dataをもとにリスクの評価を行い、結果を取得します |
| Capy処理 | リスクベース認証承認処理 | CapyRiskbasesApprove | capy_dataをもとに評価結果の承認を行います |
| Capy処理 | パズルキャプチャ評価処理 | CapyPuzzleCaptchaEvaluate | capy_challengekeyとcapy_answerをもとに評価を行います |
| Capy処理 | リアルタイムブラックリスト評価処理 | CapyBlacklistEvaluate | ブラックリストのIPアドレスに基づき、評価を行います | |
| TOTP処理 | TOTP認証コード生成処理 | TotpGenerate | TOTP認証で認証を行うために必要な、QRコード、シークレットキーを生成し、返却します |
| TOTP処理 | TOTP検証処理 | TotpVerify | 送信されたTOTPコードが正しいかを評価します |
| TOTP処理 | TOTP削除処理 | TotpRemoveAll | TOTP認証の設定情報を削除します |
| 本人確認処理 | 本人確認（マッチング）処理 | CustomerinfoMatch | docomoまたはauIDの本人確認結果を返却します |
| docomo処理 | dConnectのauthorizationエンドポイント接続処理 | ClaimsProvider/dConnect | docomoのdConnect APIの認証エンドポイントに接続し、認証リクエストを行います |
| docomo処理 | dConnectのauthorizationエンドポイント応答処理 | ClaimsProvider/DCAuthresp | dConnectの認証エンドポイントからの応答を受け取ります |
| docomo処理 | dConnectのTokenendpoint接続処理 | ClaimsProvider/DCToken | dConnect APIのトークンエンドポイントに接続して、アクセストークンを取得します |
| auID処理 | auID本人確認処理 | ClaimsProvider/AuIDAuthorize | auIDの認証エンドポイントに接続して、ユーザーの認証を行います |
| GooglereCAPTCHA検証処理 | Google reCAPTCHA 検証処理 | GoogleRecaptchaSiteverify | アクセスが人間かボットかを検証します |
| FIDO2処理 | パスキー登録時challenge取得処理 | MakeCredentialOptions | 登録プロセス時に必要なチャレンジを取得します |
| FIDO2処理 | パスキー登録処理 | MakeCredential | ユーザーのパスキー認証情報を登録します |
| FIDO2処理 | パスキー認証時Challenge取得処理 | MakeAssertionOption | パスキー認証の際に必要なチャレンジを取得します |
| FIDO2処理 | パスキー認証処理 | MakeAssertion | パスキー認証を使用して、ユーザーの認証を行います |
| Yahoo!JAPAN OIDC接続処理 | Yahoo!JAPAN authorizationエンドポイント接続処理| ClaimsProvider/YJAuthorize | Yahoo! JAPANのOpenID Connect（OIDC）の認証エンドポイントに接続して、ユーザーの認証を行います |
| LINE処理 | 連携アプリ削除処理 | ClaimsProvider/LINE/RevokeAuthority | 対象LINEアカウントからSELMIDへの連携許可を取り消します |
| xID処理 | Userinfo拡張 | ClaimsProvider/xID/userinfoEx | xID Userinfo (利用者情報)処理を実施し識別に必要な最低限のユーザ情報を返却します |
| xID処理 | Userdata拡張 | ClaimsProvider/xID/userdataEx | xID Re-Verification (本人確認情報更新)、xID Re-VerificationStatus (本人確認情報更新状況参照)、xID Userdata (個人情報)のAPIを実行し、本人確認情報更新および利用者の個人情報取得を返却します |
| xID処理 | Serial Request拡張 | ClaimsProvider/xID/serial/requestEx | xID Serial (利用者証明用証明書シリアル)、xID Re-Verification (本人確認情報更新)、xID Re-VerificationStatus (本人確認情報更新状況参照)のAPIを実行し、シリアル番号の提供を利用者にリクエストおよび本人確認情報の更新を行います |