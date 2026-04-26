## SIADS 699: Getting Started in the Cloud

One challenge a lot of teams encounter in their capstone project is sharing data. In the past we've seen teams send CSVs via slack, upload massive files to git, and some store their data in Google Drive. 

I think AWS is the best way to share data among your team. Here we'll discuss some benefits of doing so, while also acknowledging some tradeoffs of using AWS for your project. 

**If you are interested in reading and writing files to the cloud while working in your local VS Code then this setup is for you.**

- Module 0: [Do You Need the Cloud?](https://github.com/chrismca13/aws-demo/tree/main/0_Do-you-need-the-cloud)
- Module 1: [Setting up the AWS Account](https://github.com/chrismca13/aws-demo/tree/main/1_setting_up_the_aws_account#siads-699---module-1-download-setting-up-the-root-user)
- Module 2: [Setting up the Admin Role](https://github.com/chrismca13/aws-demo/tree/main/2_setting_up_the_admin_role#siads-699---module-2-setting-up-admin-access)
- Module 3: [Setting up the Team Accounts](https://github.com/chrismca13/aws-demo/tree/main/3_setting_team_accounts#siads-699---module-3-setting-up-admin-access)
- Module 4: [Accessing S3 from VS Code ](https://github.com/chrismca13/aws-demo/tree/main/4_accessing_S3_from_VS_code)
- Module 5: Setting up Spending Threshold Alerting. 


After your complete the steps above, your team will be able to write and read from the cloud with a single line of code like this:


* Saving a dataframe to the cloud:
```python
import pandas as pd
import numpy as np

# Create a fake dataframe with 10 records
np.random.seed(0)
df = pd.DataFrame({
    'feature_1': np.random.rand(10),
    'feature_2': np.random.rand(10),
    'feature_3': np.random.randint(0, 100, 10),
    'feature_4': np.random.choice(['A', 'B', 'C'], 10),
    'target': np.random.randint(0, 2, 10)
})

# Save data to S3
df.to_csv("s3://umich-capstone-project/data.csv", index=False)
```

* Reading data from the cloud:
```python
import pandas as pd

# Read data from S3
df = pd.read_csv("s3://umich-capstone-project/data.csv")
```