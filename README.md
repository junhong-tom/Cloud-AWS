# Cloud-AWS
AWS-雲端

AWS 文件
尋找使用者指南、開發人員指南、API 參考資料、教學等。
https://docs.aws.amazon.com/zh_tw/index.html 

Acount Root User:
1. 申請 AWS 帳號後，帳號就是 Acount Root User (權限特大)
   Account Number
   The Aws root user credentials.
  
  You must understand the various types of AWS security credentials and how to manage them.
  必須了解不同類型的 Security Credentials 及如何管理 Credentials
  
  Credentials = (身分 identity,權限 permissions )
  
  Two Types of security credentials:
  1. (username,password) => logging into the AWS Management Console
  2. access keys => help you make programmatic calls to Aws API operations and run AWS CLI
  
 
 根帳號使用者，使用 email 及 密碼，登入管理介面網頁 (Management Console -- Web Pages)，具有最高存取權限
  Account ----  credential (root user credentials) = (username -- email, password) => sign in to Web Pages => Management Console
          |_ _  all powerful 
          
  MFA = Multi-Factor Authentication => 額外的安全保障
  Aws recommends that you require MFA on the AWS account root user credentials and privileged 特權 IAM users. 
  (建議啟用 MFA 功能) 帳號 及 特權使用者
  
  IAM helps you secure and control access to AWS services and resources.
  
  目標: 
  First, create an IAM User and grant that user full access to Aws. 創建一位有最高授權的使用者
  Then use this user's credentials to work with AWS. 操作AWS
  - As an IAM user, you can sign in to the AWS web pages, the AWS Management Console, and the AWS Support Center, just as you can as th AWS root user.
    如同根使用者一般，登入 AWS 或 使用 Support Center
  - You can create multiple IAM users, each with access to specific AWS resources. To further restict access, you can create as many IAM users as necessary with read-only access to your AWS resources.
    針對特定的資源，創建使用者並設定相對應的存取權限
    
Access Keys and Key Pairs
存取金鑰 及 金鑰對
Access Keys: for api calls (authenticate)
You must use access keys for programmatic access to AWS services and resources and to use the AWS CLI.
Access Keys = (An access key ID, A secret access key)
- If you lose or forget your access key, you can create a new set of access key.
  重建 access key (遺失或忘掉)
- Having a maximum of two access keys at any time
  最多兩組
- You can create access keys from the AWS CLI and from the AWS Management Console.
  透過 CLI 或 Console 產生 access keys
- You can create temporary access keys (which include a security token that must be sent to AWS when using the credentials) for use in less
  secure environments or when you want to grant users temporary access to resuources in your AWS account.
  臨時的access keys

Key pairs: Linux base for loggin
Consist of a public key and a private key
You use key pairs to access Amazon EC2 instances and Amazon CloudFront.
- A key pair is a pair of text files: a public key and a corresponding private key.  The strings inside the private and public key text files
  are randomly generated numbers and characters, which makes them difficult to guess.
  金鑰對是兩個文字檔，分別稱為公鑰及對應的私鑰，檔案其中的字串分別為隨機產生的數字與字元
- The private key helps you creat a digital signature.
  私鑰成為數據簽章
- AWS uses the corresponding public key to validate this digital signature.
  AWS使用對應的公鑰，用來驗證私鑰(數據簽章)
- To create your own key pairs.
  EC2:         ==> To enable access to the EC2               ==>    To create this from the EC2 console, the CLI, or via an API
  EC2 的金鑰對用來存取 EC2 ，可以透過 EC2 的 Console 或 指令 或是 透過 API
  CloudFront:  ==> To create signed URLs for private content ==>  To create this from Security Credentials page in the AWS Management Console
 CloudFront 的金鑰對用來產生 signed URLs ，發佈有限制的 content (內容)
 
 AWS Management Console
 - A web application = To help you manage various AWS service
 - A simple and convenient user Interface for each service.


  


AWS 官網建議: Root Acount User 應該只執行的任務而非甚麼都可以去執行。
https://docs.aws.amazon.com/zh_tw/general/latest/gr/root-vs-iam.html
英文版
https://docs.aws.amazon.com/general/latest/gr/aws-general.pdf#root-vs-iam
中文版
https://docs.aws.amazon.com/zh_tw/general/latest/gr/aws-general.pdf#root-vs-iam

一 使用者分為:
1.  擁有 AWS 帳號的使用者  
2.  IAM 使用者
    2.A   登入
    2.B   操作 <== 與權限有關 -- 使用適當權限的 IAM 使用者來執行任務及存取資源 
    (We recommend that you use an IAM user with appropriate permissions to
     perform tasks and access AWS resources)
二 所有使用者階有安全憑證 (All AWS users have security credentials.)

Tasks
• 更改帳戶設定 ( Change your account settings.) <== (root user credentials)
  -  需要   Root Acount User
            account name, 
            email address, 
            root user password,
            root user access keys
  -  不需要 Root Acount User
            聯絡資訊 ( contact information )
            付款貨幣偏好設定和地區 ( payment currency
            preference, and Regions)
            
• 還原 IAM 使用者許可 (Restore IAM user permissions.)
  - IAM 管理員的許可，只能透過 Root Account User 根使用者身分登入並且編輯政策
    和還原這些許可 (If the only IAM administrator accidentally revokes their own
    permissions, you can sign in as the root user to edit policies and restore
    those permissions. )
    
• 啟用 IAM 帳單和費用管理面版 ( Activate IAM access to the Billing and Cost
  Management console. )
  
• 檢視特定稅務發票 (View certain tax invoices.)
  An IAM user with the aws-portal:ViewBilling permission can view and
  download VAT invoices from AWS Europe, but not AWS Inc or Amazon Internet
  Services Pvt. Ltd (AISPL).
• 關閉帳號 (Close your AWS account.)
• 更改或取消 AWS 支援計畫 ( Change or Cancel your AWS Support plan. )
• 在預留執行個體市場註冊為賣方。(Register as a seller in the Reserved Instance
  Marketplace.)
• 設定 S3 儲存貯體的MFA Delete 功能。(Configure MFA delete for your S3 bucket.)
• 編輯或刪除 Amazon S3 儲存貯體政策，其中包含無效 VPC 端點 ID 或 VPC 端點 ID 的
  Amazon S3 儲存貯體政策。(Edit or delete an Amazon S3 bucket policy that
  includes an invalid VPC ID or VPC endpoint ID. )
• 註冊 GovCloud。(Sign up for GovCloud.) <br>

實驗 0001 -- 申請帳號 Root Account User 

實驗 0002 -- 操作 IAM : 創建一位具有管理者權限的 IAM User 替代 Roor Account User (無群組)

AWS 官網建議: [IAM 中的安全最佳實務](https://docs.aws.amazon.com/zh_tw/IAM/latest/UserGuide/best-practices.html)
建議:
• 使用暫時性憑證存取
  要求人類使用者搭配身分提供者使用聯合功能，以便使用暫時性憑證存取 AWS
• 使用 IAM 角色的暫時性憑證  
  要求工作負載使用 IAM 角色的暫時性憑證存取 AWS
• 多重要素驗證
  需要多重要素驗證 (MFA)
• 定期輪換存取金鑰 -- 長期憑證的使用
  對於需要長期憑證的使用案例，請定期輪換存取金鑰
• 根使用者憑證的保護 
  保護您的根使用者憑證，不要將其用於日常任務
• 最低權限許可
  套用最低權限許可
• 使用 AWS 受管政策
  開始使用 AWS 受管政策並朝向最低權限許可的目標邁進
  使用 IAM 政策中的條件進一步限制存取權
• 定期檢閱並移除未使用的使用者、角色、許可、政策和憑證
• IAM Access Analyzer
  使用 IAM Access Analyzer 根據存取活動產生最低權限政策
  使用 IAM Access Analyzer 驗證對資源的公開與跨帳戶存取權
  使用 IAM Access Analyzer 驗證 IAM 政策，確保許可安全且可正常運作
• 建立跨多個帳戶的許可防護機制
• 使用許可界限委派帳戶內的許可管理

實驗 0003 -- 停用、刪除 Roor Account User 和 代理人的憑證

實驗 0004 -- 新增授權群組 IAM Group

實驗 0005 -- 操作 IAM : 創建一位 IAM User 透過 IAM Group 授權

實驗 0006 -- 操作 IAM : 創建一位 IAM Group + 創建 IAM Group 並授權

實驗 0007 --  IAM 密碼政策




