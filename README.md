# 🌐 Building a Language Translation Bot using Amazon Lex

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

## Specify Intents and Slots 🎯

### Key Terms

- **Intent:** User goal
- **Utterance:** User input
- **Slot:** Variable extracted from input
- **Fulfilment:** Chatbot action/response

**Example in Amazon Lex Documentation:**

- Hotel Booking Chatbot: Intent = BookHotel, Utterance = "book a hotel", "new york", "November", Slots = City, CheckInDate, Fulfillment = confirmation message

![Structure](Images/structure.png)

---

## Now Let's Create our Language Translator Bot

---

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
