## アプリケーション連携  

### アプリケーションの構成の決定  
- 種類  
  - Confidentialクライアント：Webサービスなど、client_secretを安全に保存できるサービス  
  - Public：ネイティブ、SPAなどclient_secretの安全に保存できないサービス  
- 言語、フレームワーク  
  - 利用するライブラリの検討  
    [公式ページ](https://docs.microsoft.com/ja-jp/azure/active-directory/develop/reference-v2-libraries)  

### Azure AD B2C側の設定   
- アプリケーションの登録  
  - client_id、client_secretの取得  
  - Redirect_uri：認証完了後、リダイレクトするアプリケーションのURL  
- アプリケーションから呼び出すポリシーの決定  
  - 呼び出すUserJourneyの決定  
  - アプリケーションへ返却する属性の決定  
  - シングルサインオンの構成（強制再認証の有無など）  

### アプリケーション側の設定/実装
- Client_id, client_secret、Azure AD B2Cのエンドポイント（ポリシー単位）の指定  
- ライブラリを使わない場合やライブラリの種類によっては以下を忘れずに実装する必要あり  
  - id_tokenのValidation
  - ポリシーのアクション結果のハンドリング
    - （例：Signinポリシーからpassword resetポリシーへの推移を行う際は、Signinポリシーから返ってくるエラーメッセージをハンドリングしてPassword resetポリシーを呼び出す処理が必要）

