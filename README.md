# How to add extension for automation test in UnitTest for [LambdaTest](https://www.lambdatest.com/?utm_source=github&utm_medium=repo&utm_campaign=UnitTest-add-extension)

If your webapp requires an extension for automation test in UnitTest on Lambdatest, you can use the following steps to upload extension and run your test. You can refer to sample test repo [here](https://github.com/LambdaTest/Python-UnitTest-Selenium).

# Steps:

## Step 1: Get the zip file (Skip this if you already have the zip file with you)

Note: You will need the Chrome Extensions's ID for this. I am referring it to as $ID$. You can get the $ID$ from the URL of the Chrome Extension page.
1. Install your desired chrome extension on chrome.
2. Go to Chrome's Extensions page (chrome://extensions/), Enable the developer mode (check the developer mode box) and take note of the ID for your desired extension.
3. Your extension will be located at:

For Unix, ~/.config/google-chrome/Default/Extensions/$ID$

For Windows, C:\Users\<Your_User_Name>\AppData\Local\Google\Chrome\User Data\Default\Extensions\$ID$

For OSX, ~/Library/Application Support/Google/Chrome/Default/Extensions/$ID$

## Step 2: Upload the zip file to LamdbaTest using API

1. * [Use the LambdaTest extension upload API to upload the zip file to the backend.](https://www.lambdatest.com/support/api-doc/#/extensions/UploadExtensions)

2. Copy the link to your extension which will look something like - https://automation-prod-user-files.s3.amazonaws.com/extensions/orgId-XXXX/2.1.0_0.zip

## Step 3: Pass extension in capabilities

In the test file, you need to update the test capabilities and add the extension capability. For example:

```python
desired_caps = {
            'LT:Options': {
                "build": "Python Demo",  # Change your build name here
                "name": "Python Demo Test",  # Change your test name here
                "platformName": "Windows 11",
                "selenium_version": "4.0.0",
                "lambda:loadExtension": "https://automation-prod-user-files.s3.amazonaws.com/extensions/orgId-XXXX/2.1.0_0.zip"
            },
            "browserName": "Chrome",
            "browserVersion": "98.0",
        }

```

## Step 4: Run your test

```bash
python lambdatest.py
```


# Links:

[LambdaTest Community](http://community.lambdatest.com/)

