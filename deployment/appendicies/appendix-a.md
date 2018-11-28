## Appendix A - Creating a Deployment Package with Python

How to create a deployment package for Lambda using python
For detailed information, refer to our web page at http://docs.aws.amazon.com/lambda/latest/dg/lambda-python-how-to-create-deployment-package.html

For a quick cheat sheet, as python environment in lambda does not have all the library user can possibly use, it is recommended that you use a customized deployment package for any function that extends beyond built-in AWS SDK.

In our case, we created the project directory, and using pip, installed the necessary library into the project directory, and zipped the directory as is.

From CLI, the sequence of commands should look like this.

```python
mkdir project
cd project
vi Scoring.py
pip install redis –t .
pip install boto3 –t .
zip –r LambdaDeploy.zip *
```
For more information on creating a proper deployment package, please refer to the link above.
