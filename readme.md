# Integrating eSewa Payment Gateway (new) using JavaScript

This guide covers two approaches to integrate the eSewa payment gateway into your web application using JavaScript. The first approach generates the payment signature directly within JavaScript, while the second approach involves calling an API to generate the signature.

## Approach 1: Generating Signature within JavaScript

In the `withAPI.html` file, we demonstrate how to generate a payment signature directly within JavaScript. This method is suitable for scenarios where you can securely store and use your secret key on the client side. However, this is generally not recommended due to security concerns, as exposing your secret key can lead to unauthorized transactions.

### Key Steps:

1. Calculate the signature using the HMAC-SHA256 algorithm, provided by the CryptoJS library.
2. Use the generated signature to fill in the payment form.
3. Submit the form to eSewa's payment URL.

### Pros and Cons:

- **Pros**: Simplifies the process by eliminating the need for server-side signature generation.
- **Cons**: Exposes your secret key, making it vulnerable to security risks.

## Approach 2: Generating Signature via API

The `withoutAPI.html` file illustrates how to generate a payment signature by calling a backend API. This method is more secure as it keeps your secret key on the server, away from the client side.

### Key Steps:

1. Send a request to your backend server with the necessary payment details.
2. Your server generates the signature using the secret key and returns it in the response.
3. Use the received signature to fill in the payment form.
4. Submit the form to eSewa's payment URL.

### Pros and Cons:

- **Pros**: Enhances security by keeping your secret key on the server.
- **Cons**: Requires additional backend setup to handle signature generation.

For detailed payment integration steps and parameters, refer to the [eSewa Developer Guide](https://developer.esewa.com.np/#/epay?id=payment).

## Conclusion

Choosing the right approach depends on your application's architecture and security requirements. For most use cases, generating the signature via an API (Approach 2) is recommended to ensure the security of your payment transactions.