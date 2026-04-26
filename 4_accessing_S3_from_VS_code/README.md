## SIADS 699: Using S3 from VS Code
Now that your roles are created and you gave your team access to S3, you can read share datasets from local VS code!

### Logging in to AWS from VS Code
1. Open the terminal window in VS code (command + J on Mac)
2. Type ```aws configure``` into your terminal. This will prompt you for the following pieces of information. Fill them out:

```bash
# Enter your details when prompted:
# AWS Access Key ID: YOUR_ACCESS_KEY (from the CSV you downloaded for yourself)
# AWS Secret Access Key: YOUR_SECRET_KEY (from the same CSV)
# Default region name: us-east-2
# Default output format: json
```
- If this errored out, make sure you downloaded the `AWS CLI` package [listed as a pre-requisite in module 1. ](https://github.com/chrismca13/aws-demo/blob/main/1_setting_up_the_aws_account/README.md#pre-requisites)

3. Let's test the connection!

* Fire up a jupyter notebook and run this code to test saving a CSV to the cloud:

```python
from sklearn.dummy import DummyClassifier
from sklearn.model_selection import train_test_split
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

df.to_csv("s3://umich-capstone-project/data.csv", index=False)
```

* After your team gets access, try running this code:
```python
import pandas as pd

df = pd.read_csv("s3://umich-capstone-project/data.csv")
```

If you have any questions or feedback please post them in the SIADS 699 channel or DM me (Chris McAllister) and we'll help get things sorted out. 

If this was interesting to you at all and you'd like to know more about the cloud, a good way to learn more is by obtaining [AWS Certifications.](https://aws.amazon.com/certification/)

The `Certificed Cloud Practioner` --> `AWS Certified Machine Learning Engineer` --> `Certified Data Engineer` is a great path to focus on after you complete the MADS program. Good luck!