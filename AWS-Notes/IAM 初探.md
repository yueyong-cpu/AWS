-Q1：root user 跟 iam user 的差別？
A：root user是使用者在AWS裡創建的第一個帳號，也被稱為根用戶，擁有最高的權限，一般情況下，root user都建議開啟MFA的認證，防範被盜用而燒錢
   IAM user是由root user或是被授權的IAM user所創建的
   IAM user登入AWS需要account ID、username、password這三個
   IAM user可以被root user加進其他的group裡面，也可以限制IAM user只能操作某部分的policy(例如S3的存取權限這樣的)
   IAM user預設沒有權限，只能更改自己的密碼，需要root user授權

-Q2：user, group, role, policy 彼此間的關係為何？policy的格式為何？
A：policy，最根本的規則，住要為attach到其他人身上
   user，有以特定的policy去給予權限的使用者
   group，一群的user，給予policy後，裡面的每個人就有相同的權限了
   role，虛擬的user，需要policy去給予權限，使其可以附加到特定的服務上

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
   
