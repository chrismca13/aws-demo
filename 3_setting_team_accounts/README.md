## SIADS 699 - Module 3: Setting up Admin Access
Now that you have your admin role ready we're going to create accounts for you and your team. 

### Setting up your team's access group.
0. You should still be logged in to the `admin-role` from the previous section. Next we'll follow a similar series of steps to create accounts to get your team set up.
1. Search `IAM` again and click on the `IAM` service.
2. Click `IAM user groups` on the left side panel.
3. Click `Create group`. This time we're going to give S3 access to your team so you can easily share datasets.
4. This part is **VERY important.** Here we have two options. We can either give the team full read and write access to S3, or just read access. 
    * Giving them write access opens the possibility to store a massive dataset in S3, meaning you (as the admin / root user) would get billed for it. 
    * Giving them read access only means they won't be able to contribute to dataset creation. 
    * I recommend giving full access since S3 storage is very cheap and the odds of incurring a big bill are low, but know that you're opening yourself up to risk of losing money. 
4. Assuming you want to give your team read and write access give the name `full-s3-access` to user group, do not check any of the users in the second box, check the box next to `AmazonS3FullAccess` policy, and click the `Create user group`. It should look like this when you're done:
    * If you only want to provide only read access, simply check the box next to `AmazonS3ReadOnlyAccess` instead. Update the name of the role too so it says `read-s3-access`

![alt text](images/s3-access-group.png)

### Setting up your team's accounts.
1. Go back to `IAM` and click the `IAM users` on the left side panel.
2. Click the orange `Create user` button in the top left
3. Here you'll create an account for you teammate. Call it something like `firstname-lastname-MADS`. Click next.
4. Give them access to the s3 policy you chose above by checking the box next to the User Group and click next.
5. Click the orange `Create user` button in the bottom right. 
6. Repeat steps 2-5 for all team members on your team.

### Giving you team access to S3:
1. Go back to `IAM` and click `IAM users` on the left side panel.
2. Click the blue link on you teammates name:
![alt text](images/click-user.png)

3. Click the `Security credentials` banner across the top and click the `Create access key` button about halfway down the page:
![alt text](images/access-key.png)

4. Click the `Command Line Interface (CLI)` circle under "Use case", check the box at the bottom, and click `Next`

5. Type in a description for the key. Something like `FirstName_LastName_key` is great.

6. You won't be able to generate this key again, so it's very important you don't lose it. Like before I recommend click the `Download .csv file` button and sharing it with your teammate.

![alt text](images/access-key-download.png)

7. Repeat steps 1-6 for all of your teammates.

### Giving yourself access to connect to S3 locally in VS Code. These steps are similar to what you did before, but now you're doing it for you admin role.
1. Go back to `IAM` and click the `IAM users` on the left side panel.
2. Click the blue link on your `admin-role` name.
3. Click the `Security Credentials` again.
4. Click `Create access key`
5. Fill in the `Command Line Interface (CLI)` bubble, check the box at the bottom, and click Next
6. Give it a description, something like `admin_role_CLI_access`
7. Download the access Key as a CSV, and keep it somewhere safe. We'll need it for our next step. 
