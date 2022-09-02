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
 
 Accessing AWS Services the Right Way
 - AWS recommands that you connect as an IAM user tather than connect with your default AWS Account root user credentials.

You should create an IAM user (instead of a role) in the following cases:
使用 IAM User 而非 IAM Role
- You created an AWS account and you're the only person who works in that account. 
  初次建立帳號，尚未建立任何帳號前
- Other people in your group need to work in your AWS account, and your group is using no other identity mechanism.
  沒有使用其他身分驗證機制，但同組同仁需在你的 AWS 帳號下工作
- You want to use the CLI to work with AWS.
  使用 CLI 操作 AWS 

Create an IAM role (instead of a user) in the following cases:
使用 IAM Role 而非 IAM User
- You're creating an application that runs on an EC2 instance and the application makes requests to AWS.
  在EC2中開發應用程式，同時應用程式向AWS 發出 requests
- You're creating an app that runs on a mobile phone and makes requests to AWS.
  開發應用程式，同時應用程式向AWS 發出 requests
- Users in your company are authenticated in your corporate network and want to be able to use AWS without having to sign in again -- that is, you want to 
  allow users to federate into AWS.
  外部授權並要登入 AWS
  
實作登入 
1. -- Console
      A. Creating An IAM User
         root user (root user e-mail, password) loggin in 
         IAM 儀表板 --  create a new IAM User as administrator
         命名 
         憑證類型
         密碼 -- 密碼政策
         許可 permission Next -- 預設 full permission
         標籤
         檢閱
         Finial => 開始建立使用者
         使用者登入網址: AWS 管理主控台存取的使用者能夠登入：https://[Account ID | Account Alias].signin.aws.amazon.com/console
         access keys => 下載
      B. Logging In as the New IAM User
         使用者登入網址: AWS 管理主控台存取的使用者能夠登入：https://[Account ID | Account Alias].signin.aws.amazon.com/console
         修改密碼
         The navigation bar will show "UserName@[Account ID | Account Alias]"
         
         To Create an account alias from the IAM dashboard.
         從 IAM DashBoard 創建帳號的別名 Account alias
      C. Creating an Access Key ID and Secret Access Key (Key Pair) for an IAM User
         - 在創建 IAM User 時，Aws 會自動產生 the Access Key ID 存取金鑰 and a Secret Access key 私密存取金鑰.
         - Open the IAM console
         - Select Users
         - Select Security Credentials, and then, select Create Access Key
         - Download the Access Keys by choosing Download .csv File
         
         This is the only time you can download or view the secret access keys.
         CLI 創建 A
         $ aws iam create-access -key -user-name sam_alapati
      
      D. Using a Key Pair to Connect to an EC2 Instance
         金鑰對 Key Pair 透過 SSH 登入 EC2 及 To Perform certtain tasks with CloudFront
         Createing a Key Pair
         - 在 EC2 創建時，AWS 會去產生 Key pair 並把 Key Pair 中的公鑰嵌入 EC2 中。同時使用者必須下載私鑰 private key 
           並儲存在要連入 EC2 的機器中。
         - 金鑰對屬於 Region 服務級別。( A key pair is specific to a region.) 既如果發佈一個多區域的 EC2 實體，使用者
           必須對每個區域 Region 中個別創建 金鑰對 Key Pair
         - Security Group:
           在產生金鑰對之前，會需要指定 Security Goup 控制封包進出 inbound and outbound traffic , 如果沒有指定 Security Group
           會使用預設的 Security Group
         - Follow these steps to create a key pair. 
           1. Open EC2 Console  
           2. select a region & Create Key Pair
           3. Name Key Pair ==> You must provide the name of your key pair when you launch an EC2 instance.
           4. Download the private key file
           5. Connect to EC2 via SSH
         - Update a key pair to AWS  
           #  參考另一本書

         
3. -- CLI
      透過 CLI 這一個工具，可以幫助控制存取 AWS 的服務  The Aws CLI is a tool that helps you control multiple AWS services from the command line.
      CLI 透過公開的 API 方式，來連入 AWS 的服務  The CLI connects to the AWS servics through the public APIs of the services.
      AWS CLI 是由 Python SDK 建構的套件，既稱為 Boto The AWS is built on top of the AWS SDK for Python, all called Boto.
      CLI 可以完成如同操作 Console 達成的功能  You can achieve the same functionality with AWS CLI that you do with the AWS console.
      A. The Structure of AWS CLI Commands
         $aws s3 cp myvido.mp4 s3://samalapati/
      B. 安裝 AWS CLI (Installing AWS CLI)
         https://docs.aws.amazon.com/zh_tw/cli/latest/userguide/getting-started-install.html  
         CLI is Python-based 
         To check Python Version
         AWS CLI comes already installed on the Amazon Linux AMI.
      C. 設定 CLI (Configuring the AWS CLI)
         在使用 CLI 之前，需要先設定。 Before you can start using the AWS CLI, you must configure it.
         $aws configure
         - Information:
         - Access Key ID and Secret Access Key
         - Default Region
         - Default output Format
         
      D. 設定檔和憑證檔儲存位置 Where AWS CLI Stores the Configuration and Credential Files
         - 位置在家目錄中的 .aws 子目錄中   It stores the file under your home directory, in the .aws subdirectory
         - 檔案: ~\.aws\config & ~\.aws\credentials  Can view the configuration and credentials files 
         
      E. Using Named Profiles
         - Instead of all users using the same default profile "$HOME/.aws", you can create custom profiles with 
           different credentials, regions, and output formats.   
         - You can create any number of profiles you need.
         - Profiles help you grant separate sets of privileges for different environments, such as development and 
           production environments.
         - You can create a profile and assign it to multiple accounts.
         - Creating and using multiple profiles helps you implement different configurations for different sets of users.
         
      F. Creating a Custom Profile Using the Config and Credentials Files
      ~\.aws\config
      [default]
      region=us-west-2
      output=jaon
      
      [profile user2]
      region=us-east-1
      output=text
      
      ~\.aws\credentials
      [default]
      aws_access_key_id=
      aws_secret_access_key=
      
      [user2]
      aws_access_key_id=
      aws_secret_access_key=
      
      How to specify a named profile (user2) when executing an AWS CLI command
      $
      
      How to create a profile by editing the config and credentials files.
      $aws configure --profile use2
      
      
      G. Configuring the CLI to Use a Role
      H. Specifying Environment Variables to Configure AWS CLI
      I. Configuration Precedence
      J. Using the AWS CLI
      K. AWS CLI Command Structure
      L. Getting Help Regarding the Commands
      M. Controlling the Command Output
      N. Connecting to a Running EC2 Instance from the Command Line.
      O. Connecting from Another Server
      P. Getting the DNS of a Server
5. -- SDK
      A. AWS SDKs and Python Boto3
      B. Installing Boto3
      C. Setting UP Credentials
      D. Testing the Boto3 Installation





  


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




