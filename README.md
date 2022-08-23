# Cloud-AWS
AWS-雲端

AWS 文件
尋找使用者指南、開發人員指南、API 參考資料、教學等。
https://docs.aws.amazon.com/zh_tw/index.html 

Root Acount User:
1. 申請 AWS 帳號後，帳號就是 Root Acount User (權限特大)


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

實驗 0002 -- 操作 IAM : 創建一位具有管理者權限的 IAM User 替代 Roor Account User

AWS 官網建議: [IAM 中的安全最佳實務](https://docs.aws.amazon.com/zh_tw/IAM/latest/UserGuide/best-practices.html)




實驗 0003 -- 操作 IAM : 創建一位 IAM User 

實驗 0004 -- 操作 IAM : 創建一位 IAM Group

實驗 0004 -- 操作 IAM : 創建一位 IAM Group




