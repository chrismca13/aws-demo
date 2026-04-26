## SIADS 699: Setting up Spend Alerts
Now that you've got your team set up, you've tested the connection, and everything is working it's time to take some steps to reduce the likelihood of you getting a huge AWS bill. 

Like we said before, AWS is not required for this course and your instructors, the University of Michigan, and the MADS program are NOT responsible for any bills you rack up in AWS. 

### Setting up a Budget Alert:

1. Sign out of the `admin-role` 
2. Log in as the root user you set up way back in Module 1.  
3. Search for `Billing and Cost Management` in the search bar above and click it.
4. Click `Budgets` on the side panel on the left. Everything should look like this at this point:
![alt text](images/budgets.png)
5. Click the orange `Create budget` button in the top right. 
6. On the next page only change the following:
- Update the budget name to whatever you want, I called mine `My $0.05 Budget Alert`
- Update the `Email Recipients` to whatever email you check most frequenty. 
- The set up should look like this:

![alt text](images/budget-setup.png)

7. Click the orange `Create budget` button at the bottom right. 
8. Click the blue link on your newly created budget on the next page. 
9. Click the `Edit` button in the top right corner. 
10. Here you can customize to make sure you get alerted to whatever dollar amount your comfortable with. If you're only using AWS for data storage in S3, this is a good set up unders `Set budget amount`
- This will send you an email if you ever spend more than $.05 on a day:

![alt text](images/budget-amount.png)

11. Leave the other setting as is, scroll to the bottom, and click the orange `Next` button. 
12. Optionally, you can set additional alterting here that will give you an email if you start to approach the threshold you set in step 10. 
13. Next you can set up a budget action, I recommend skipping this for now and clicking `Next`
14. Click save - your budget is set up now!

With how affordable S3 storage there's a good chance you'll stay under your $.05 budget, but it doesn't hurt to have the alert just in case. 
