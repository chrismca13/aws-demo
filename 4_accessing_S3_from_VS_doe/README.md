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
- If this errored out, make sure you downloaded the `AWS CLI` package listed as a pre-requisite in module 1. 

3. safsf