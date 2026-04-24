## SIADS 699: Setting up Admin Access
Now that the Root User role is set up, you can create an admin role for you to work out of. 

### Setting up an Admin Role
It's a best practice to stay out of the root user role when possible. The first thing you should do is create an `admin-role` by doing the following:
1. Search and click on `IAM` in the search bar at the top of the home page:
![alt text](images/iam.png)

2. On the side panel on the left click `Users` and click `Create User`
![alt text](images/create_user.png)

3. Create a role named `admin-role`
4. Click the `Create Group` button on the top right of the `User Groups` box.
5. This will give you access to a bunch of pre-made access roles created by AWS. The one I recommend adding to your `admin-role` is called `AdministratorAccess`:
![alt text](images/administrator-access.png)

6. Once you create the group check the box next to it and click the orange Next button.
7. Click the Orange Create User on the next page. 

### Logging in to the Admin Role
0. It's a best practice to only log in to the root-user when you really need to. Most of your work should be done in the admin role from here on out. 
1. Click on `Users` in the side bar on the left.
2. You should see your newly created role.
3. Click on the role, navigate to the Security Credentials tab, and click the Enable Console Access button:
![alt text](images/console_access.png)
4. Click the orange Enable Console Access button. This generates your user name and one time password. Save it and don't lose it. Click the `Download .csv file` to be safe. 
5. Copy the `Console sign-in link URL` and paste it into your browser. As the admin of the project you'll be using this role throughout the project. **Favorite this link so you can easily get back to the log in**
6. Sign in with your username and password (that you hopefully downloaded) and you're in!


Next, we'll cover how to get access to S3 for you and your team so you all can easily save and share dataset. 

