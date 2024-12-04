# Multi-Factor Authentication Techniques 

Multi-factor authentication (MFA) is a method of access control where a user is granted access only after successfully presenting two or more separate pieces of evidence (factors) to an authentication mechanism. The factors include:
* Something you know (knowledge)
* Something you have (possession)
* Something you are (inherence)

## Something You Know

This factor typically involves a password or a PIN. This is the most common method of authentication. For instance:

```python
def authenticate(password, user_password):
    return password == user_password
```
A simple Python function can be used to check if the user’s entered password matches the stored password for that user.

## Something You Have

This is something the user has in their possession, like a hardware token, smart card, or a software token on a smartphone. A popular example is the Google Authenticator app which generates time-based one-time passwords (TOTP). Here's a Python snippet of a TOTP generator:

```python
import pyotp
totp = pyotp.TOTP('JBSWY3DPEHPK3PXP')
print("Current OTP:", totp.now())
```
In the above example, 'JBSWY3DPEHPK3PXP' is the shared secret key between the user and the server.

## Something You Are

This factor involves biometrics, such as fingerprints, retina, or voice recognition. These are harder to compromise but require specialized hardware. A simple example would be using Apple's Face ID in an iOS app:

```swift
let context = LAContext()
var error: NSError?

if context.canEvaluatePolicy(.deviceOwnerAuthenticationWithBiometrics, error: &error) {
    let reason = "Log in to your account"
    context.evaluatePolicy(.deviceOwnerAuthenticationWithBiometrics, localizedReason: reason) { success, authenticationError in
       DispatchQueue.main.async {
          if success {
             // user authenticated successfully
          } else {
             // there was a problem
          }
       }
    }
}
```
In this Swift code snippet, the `LAContext` class is used to handle the biometric authentication.

MFA significantly enhances security as it requires multiple methods for identity confirmation. It is widely used in many fields, especially where security is critical.