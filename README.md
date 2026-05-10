# Payment Link Generator (Toss & Kakao Pay)

This project is a simple, client-side web application that generates a payment request page with a QR code. It allows users to easily request payments via Toss or Kakao Pay by sharing a link or a QR code, which opens the respective app with pre-filled payment details.

## Features

- **Dynamic Amount**: Specify the payment amount directly in the URL.
- **QR Code Generation**: Automatically generates a QR code that points to the payment page, making it easy to share.
- **Multi-App Support**: Supports both **Toss** and **Kakao Pay** deep links.
- **No Backend Required**: The entire application runs in the browser, making it easy to deploy on any static hosting service.
- **Customizable**: Easily update the recipient's name, bank, and account number.

## How to Use

1.  **To request a payment with a specific amount**:
    - Append the desired amount to the URL. For example, to request 10,000 KRW, use a link like this:
      ```
      https://your-website.com/?10000
      ```
2.  **To request a payment without a specific amount**:
    - Use the base URL without any parameters:
      ```
      https://your-website.com/
      ```

When a user opens the link on a mobile device, they can choose to pay via Toss or Kakao Pay. If they open it on a desktop, they can scan the QR code with their phone to open the page and then select their preferred payment app.

## Setup for Developers

This is a client-side application with no build process. To run it locally or deploy it, you can follow these steps:

1.  **Clone the repository**:
    ```bash
    git clone https://github.com/your-username/toss-payment-generator.git
    ```
2.  **Serve the files**:
    - You can use any simple HTTP server to serve the `index.html` and `qrcode.js` files. For example, if you have Python installed, you can run:
      ```bash
      # For Python 3
      python -m http.server
      ```
    - Or, if you use Node.js, you can install `http-server`:
      ```bash
      npm install -g http-server
      http-server
      ```
3.  **Open in your browser**:
    - Navigate to `http://localhost:8000` (or the port your server is running on) to see the application.

## Customization

To customize the payment page with your own information, you will need to edit the `index.html` file.

1.  **Recipient's Name**:
    - In `index.html`, find the `<h1>` tag and change `???` to the name of the person or entity receiving the payment.
      ```html
      <!-- Before -->
      <h1>???에게 송금하기</h1>

      <!-- After (Example) -->
      <h1>Jules에게 송금하기</h1>
      ```

2.  **Bank and Account Information**:
    - In the `<script>` section at the bottom of `index.html`, update the `BANK_NAME`, `ACCOUNT_NUMBER`, and `BANK_CODE` constants with your own information.
      ```javascript
      // --- Configuration ---
      // TODO: DEVELOPER - Set your bank name, account number, and bank code.
      const BANK_NAME = "토스뱅크"; // Change this to your bank name
      const ACCOUNT_NUMBER = "100012345678"; // Change this to your account number
      const BANK_CODE = "092"; // Change this to your bank's 3-digit code
      ```
    - The `BANK_CODE` is required for Kakao Pay support. Common codes (like 092 for Toss Bank, 090 for Kakao Bank) are listed in the comments of `index.html`.

## Included Library

This project uses a modified version of the [QRCode for Javascript](http://www.d-project.com/qrcode/) library to generate QR codes. The included `qrcode.js` file has been documented for clarity.

## License

This project is open-source and available under the [MIT License](LICENSE).