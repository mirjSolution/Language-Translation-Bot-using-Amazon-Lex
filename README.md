# 🌐 Building a Language Translation Bot using Amazon Lex

## Table of Contents

1.  [Project Overview ☁️](#project-overview-%E2%98%81%EF%B8%8F)
2.  [Create an Empty Chatbot 🤖](#create-an-empty-chatbot-%F0%9F%A4%96)
3.  [Specify Intents and Slots 🎯](#specify-intents-and-slots-%F0%9F%8E%AF)
4.  [Specify Fulfilment ⚡](#specify-fulfilment-%E2%9A%A1)
5.  [Create an IAM Role 🔐](#create-an-iam-role-%F0%9F%94%90)
6.  [Create a Lambda Function 🖥️](#create-a-lambda-function-%F0%9F%96%A5%EF%B8%8F)
7.  [Test the Lambda Function 🧪](#test-the-lambda-function-%F0%9F%A7%AA)
8.  [Test the Chatbot 💬](#test-the-chatbot-%F0%9F%92%AC)
9.  [Conclusion & Clean-up ✅](#conclusion--clean-up-%E2%9C%85)

---

## Project Overview ☁️

In this project, we'll be building a **language translation bot using Amazon Lex**.

**Goal:** Translate a word or sentence into another language simply by typing it into the chatbot.

### Steps to be performed 👩‍💻

1.  Create an empty chatbot
2.  Specify intents and slots
3.  Specify fulfilment
4.  Create an IAM role
5.  Create a Lambda function
6.  Test the Lambda function
7.  Test the chatbot

### Services Used 🛠

- **Amazon Lex:** Build the chatbot and define conversation flow
- **AWS Lambda:** Process translation requests
- **AWS IAM:** Secure access by managing permissions
- **Amazon Translate:** Translate text according to input language

### Estimated Time & Cost ⚙️

- **Time:** 1-2 hours
- **Cost:** Free (AWS Free Tier)

➡️ **Diagram:**

![Diagram](Images/diagram.png)

---

## Create an Empty Chatbot 🤖

1.  Login to AWS Management Console and navigate to **Amazon Lex**.
2.  Click **Create Bot** → **Create a blank bot**.
3.  Enter a **bot name** and **description**.
4.  For **IAM role**, choose **Create a role with basic Amazon Lex permissions**.
5.  Choose **No** for COPPA, leave other defaults, click **Next**.
6.  Select **language** and **voice interaction module**.
7.  Keep **Intent classification confidence threshold** default, click **Done**.

> Your empty chatbot is now created and ready for intent configuration.

---

## Specify Intents and Slots 🎯

### Key Terms

- **Intent:** User goal
- **Utterance:** User input
- **Slot:** Variable extracted from input
- **Fulfilment:** Chatbot action/response

**Example:**

- Pizza chatbot: Intent = order pizza, Utterance = "I want a large pepperoni pizza", Slots = size, toppings, Fulfilment = confirmation message

### Steps

1.  Create an **Intent**: enter name & description
2.  Add **sample utterances**
3.  Create **Slots**:

    - **Language Slot:** slot type `language`, values = French, Japanese, Chinese, Spanish, German, Norwegian
    - **Text Slot:** slot type `AMAZON.FreeFormInput`, prompt for text to translate

4.  Add additional utterances specifying slot usage
5.  Optionally add **Initial response** to intent

---

## Specify Fulfilment ⚡

1.  Fulfilment triggers the **Lambda function**.
2.  Add **success/failure prompts**.
3.  Go to **Advanced Options** → check **Use a Lambda function for fulfilment**.
4.  Add a **Closing message**.
5.  Click **Save Intent**.

> Conversation flow setup is complete. Next: Lambda function.

---

## Create an IAM Role 🔐

1.  Navigate to **IAM** → **Roles** → **Create Role**
2.  Choose **AWS service** → **Lambda**
3.  Attach policies:

    - `TranslateFullAccess`
    - `AWSLambdaBasicExecutionRole`

4.  Enter **role name & description** → **Create Role**

> This role allows Lambda to access Amazon Translate and execute.

---

## Create a Lambda Function 🖥️

1.  Navigate to **Lambda** → **Create Function**
2.  Name the function, choose **Python 3.12 runtime**
3.  Assign previously created **IAM role**
4.  Creating Lambda code:

5.  Click **Deploy**.

> Code explanation: Input extraction, language mapping, translation, response formatting, error handling.

---

## Test the Lambda Function 🧪

1.  Click **Test** → **Configure Test Event**
2.  Use event JSON format:

3.  Save → Test → Lambda outputs JSON formatted response for Lex

---

## Test the Chatbot 💬

1.  Navigate to **Intent page** of the chatbot
2.  Click **Settings** → choose **Lambda function source**
3.  Test conversations with phrases to translate into selected languages

---

➡️ **Final Result:** _(Insert screenshot or description of completed chatbot)_

---

## Conclusion & Clean-up ✅

### Conclusion

- Congratulations! Explore adding new languages or integrating the bot on a website

### Clean-up

1.  Delete chatbot: **Amazon Lex → Select Bot → Action → Delete**
2.  Delete Lambda function: **Lambda → Select function → Actions → Delete**
3.  Delete IAM role: **IAM → Select role → Delete**

---
