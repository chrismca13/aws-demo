## SIADS 699 - Module 0: Is using AWS worth the effort?

### What is AWS?
AWS is a Cloud Service Provider (CSP) that allows you to access compute power via the internet as opposed to paying for a physical machine. Competitors to AWS include Google Cloud Platform (GCP) and Microsoft Azure. 
Most companies expect their data scientists to be familiar with working in the cloud — now is a great time to start exploring the tool and all that it offers

### What is S3?
S3 is AWS's file storage solution. S3 stands for "Scalable Storage Solution," you can kind of think of it as a giant file storage system (like Finder on Mac or File Explorer on Windows).

However, the main benefit here is that you can easily share the file storage solution among your teammates, see more below. 

### Tradeoff of the Cloud
**You can rack up a bill.**
* Using AWS is NOT required for this course. The University of Michigan, the MADS program, or your instructors are NOT responsible for any fees / bills you incur in AWS.
* With that said, S3 storage is incredibly cheap. As of April 2026, they're only charging $0.023 per GB of data per month that you store in S3. 
    - At this price it would be very difficult to spend more than $5 throughout the capstone project, but it's something to be aware of.
* Check current pricing at https://aws.amazon.com/s3/pricing/

### Benefits of the cloud
* After you set it up, saving data in AWS S3 is very easy. You can easily backup data with one line of code:

```python
import pandas as pd

df.to_csv("s3://capstone-project-mcallister/teams.csv", index=False)
```
* Sharing data among your team is also very straightforward, pulling data down also only requires one line of code:

```python
import pandas as pd

df = pd.read_csv("s3://capstone-project-mcallister/teams.csv")
```

* You can do the same thing for model objects:

```python
### Create trained model object:

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

# Split out target and features
X = df.drop('target', axis=1)
y = df['target']

# Train-test split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Create and train the dummy classifier
clf = DummyClassifier(strategy='most_frequent')
clf.fit(X_train, y_train)
```

```python
### Save the model to S3

import pickle
import boto3

# Save model locally to disk
pickle.dump(clf, open('dummy_classifier_local_copy.pkl', 'wb'))

# Upload to S3
s3_client = boto3.client('s3')
s3_client.upload_file(
    'dummy_classifier_local_copy.pkl', # Name of model object in local file system
    'capstone-project-mcallister',     # Name of folder in S3
    'dummy_classifier.pkl'             # What you want the file named in S3
)

print("Dummy classifier saved to S3!")
```

* Like with datasets, anyone on your team with access to the S3 bucket can read in this trained model object now:

```python
import boto3
import pickle
import io

# Create S3 client
s3_client = boto3.client('s3')

# Download the model from S3
response = s3_client.get_object(
    Bucket='capstone-project-mcallister',
    Key='dummy_classifier.pkl'
)

# Load the model from the response
model_buffer = io.BytesIO(response['Body'].read())
clf = pickle.load(model_buffer)
```

### Another tradeoff of using the Cloud:

**It takes time to set up.**
* We'll cover it in the next module, but setting up your team in AWS takes some effort (around 40 minutes). 

--
Being comfortable in the cloud is a good skill for any data scientist - if nothing else this is a great reason to use AWS in your project workflow. If this feels worth it to you, head to [the second module](https://github.com/chrismca13/aws-demo/tree/main/1_setting_up_the_aws_account)!
