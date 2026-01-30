### 【問答題】  
### Q1：root user 跟 iam user 的差別？  
**root user**：是使用者在AWS裡創建的第一個帳號，也被稱為根用戶，擁有最高的權限，一般情況下，root user都建議開啟MFA的認證，防範被盜用而燒錢  
**IAM user**：  
    * 由 root user 或被授權的使用者所創建  
    * 登入需要：Account ID、Username、Password  
    * 預設沒有權限，需要被授權或加入 Group  

### Q2：user, group, role, policy 之間的關係？  
1. **Policy**：最根本的規則，主要為 attach 到其他人身上  
2. **User**：由特定Policy賦予權限的使用者  
3. **Group**：一群User的集合，讓裡面的人有共同權限  
4. **Role**：虛擬的User，讓服務（例如 EC2）可以取得權限  

   Policy主要是以JSON的格式撰寫，如以下允許存取S3服務的  
   ex:
   * **Policy 格式範例**
   ```json
   {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::example-bucket/*"
        }
    ]
  } 
   
### 【實作題】  
### Q1：為root account創建MFA登入。  
登入 Root Account  
在IAM Dashboard的第一個，點擊「新增MFA」
多重驗證MFA裡點擊啟動MFA  
在選擇要指派MFA裝置類型裡，點擊虛擬MFA裝置  
啟動手機中的Google Authenticator並做綁定的動作  

### Q2：創建 aws credential（access key & secret），並且使用 aws cli 嘗試存取 ec2 列表（可以手動創建一台機器）及 s3 列表。  
