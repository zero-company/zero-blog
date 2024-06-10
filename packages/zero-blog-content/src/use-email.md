https://lizenshakya.medium.com/how-to-send-mails-with-gmail-using-nodemailer-after-less-secure-app-is-disabled-by-google-b41abf3fdada

```
const nodemailer = require("nodemailer");

const client = nodemailer.createTransport({
    service: "Gmail",
    auth: {
        user: "Your email",
        pass: "Google App Password Without Spaces"
    }
});

client.sendMail(
    {
        from: "sender",
        to: "recipient",
        subject: "Sending",
        text: "Hello"
    }
)
```
