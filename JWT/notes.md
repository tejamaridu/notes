**JSON WEB TOKEN**


**What are authentication and authorization, What are the differences?**

In simple terms, authentication is the process of verifying who a user is, while authorization is the process of verifying what they have access to.

**Authentication:** 

Authentication is the process of verifying a user or device before allowing access to a system or resources. This ensures only those with authorized credentials gain access to secure systems. 

The authentication by the server is done mostly by using the *username* and *password*. Other ways of authentication by the server can also be done using cards, retina scans, voice recognition, and fingerprints.

A very common use for **JWT** and perhaps the only good one is as an API **authentication mechanism**.

**Authorization:** 

Process of determining what actions or resources a user or system is permitted to access or perform after they have been authenticated. It involves checking the permissions and privileges associated with the authenticated identity against the access control policies defined by the system.


|**AUTHENTICATION**|**AUTHORIZATION**|
| :-: | :-: |
|**Determines whether users are who they claim to be**|Determines what users can and cannot access|
|**Challenges the user to validate credentials (for example, through passwords, answers to security questions, or facial recognition)**|Verifies whether access is allowed through policies and rules|
|**Usually done before authorization**|Usually done after successful authentication|
|**Generally, transmits info through an ID Token**|Generally, transmits info through an Access Token|
|**Generally governed by the OpenID Connect (OIDC) protocol**|Generally governed by the OAuth 2.0 framework|


**What is JWT?**

A JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties (Client or Server). This information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret (with the **HMAC algorithm**) or a **public/private key** pair using **RSA or ECDSA**.


**When should you use JSON Web Tokens?**

**Authorization:** This is the most common scenario for using JWT. Once the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services, and resources that are permitted with that token. Single Sign On is a feature that widely uses JWT nowadays, because of its small overhead and its ability to be easily used across different domains.

**Information Exchange:** JSON Web Tokens are a good way of securely transmitting information between parties. Because JWTs can be signed—for example, using public/private key pairs—you can be sure the senders are who they say they are. Additionally, as the signature is calculated using the header and the payload, you can also verify that the content hasn't been tampered with.


**What JSON Web Token structure contains?**

In its compact form, JSON Web Tokens consist of three parts separated by dots (**.**), which are:

1. Header
1. Payload
1. Signature

Therefore, a JWT typically looks like the following.

`     `**xxxxx.yyyyy.zzzzz**  

**I) Header:**

The header typically consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA.

{

`  `"alg": "HS256",

`  `"typ": "JWT"

}

**II) Payload:**

The second part of the token is the payload, which contains the claims. Claims are statements about an entity (typically, the user) and additional data. There are three types of claims: registered, public, and private claims.

1. **Registered claims:** These are a set of predefined claims which are not mandatory but recommended, to provide a set of useful, interoperable claims. Some of them are: **iss** (issuer), **exp** (expiration time), **sub** (subject), **aud** (audience), and others. Notice that the claim names are only three characters long as JWT is meant to be compact.
1. **Public claims:** These can be defined at will by those using JWTs. But to avoid collisions they should be defined in the IANA JSON Web Token Registry or be defined as a URI that contains a collision resistant namespace.
1. **Private claims:** These are the custom claims created to share information between parties that agree on using them and are neither registered or public claims.

{

`  `"sub": "teja.maridu",

`  `"name": "Teja M",

`  `"iat": 1516239022

}

**III) Signature:**

To create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that. The signature is used to verify the message wasn't changed along the way, and, in the case of tokens signed with a private key, it can also verify that the sender of the JWT is who it says it is.

HMAC SHA256 algorithm, the signature will be created in the following way:

HMACSHA256(

`  `base64UrlEncode(header) + "." +

`  `base64UrlEncode(payload),

`  `SECRET\_KEY

)

![JWT.io Debugger](Aspose.Words.5d9b29ea-e0a2-4688-ae59-c79a3db86f94.001.png)


**How do JSON Web Tokens work?**

In authentication, when the user successfully logs in using their credentials, a JSON Web Token will be returned. Since tokens are credentials, great care must be taken to prevent security issues. In general, you should not keep tokens longer than required.

You also should not store sensitive session data in browser storage due to lack of security.

Whenever the user wants to access a protected route or resource, the user agent should send the JWT, typically in the Authorization header using the Bearer schema. The content of the header should look like the following:

**Authorization: Bearer <token>**

**Why should we use JSON Web Tokens?**

Let's talk about the benefits of JSON Web Tokens (JWT) when compared to Simple Web Tokens (SWT) and Security Assertion Markup Language Tokens (SAML).

As JSON is less verbose than XML, when it is encoded its size is also smaller, making JWT more compact than SAML. This makes JWT a good choice to be passed in HTML and HTTP environments.

Security-wise, SWT can only be symmetrically signed by a shared secret using the HMAC algorithm. However, JWT and SAML tokens can use a public/private key pair in the form of a X.509 certificate for signing. Signing XML with XML Digital Signature without introducing obscure security holes is very difficult when compared to the simplicity of signing JSON.

**What are public and private keys, where it used?**

In JWT (JSON Web Tokens), public key and private key pairs are typically used in **asymmetric encryption** algorithms such as RSA or ECDSA to secure the tokens. Asymmetric encryption involves the use of two keys: a public key and a private key. Here's how public and private keys are used in JWT:

1. **Token Generation**: When a JWT is generated, it can be signed using either a private key (for RS256, RS384, RS512, ES256, ES384, ES512 algorithms) or a shared secret key (for HMAC algorithms). If a private key is used, it's kept secret by the issuer and is used to generate the digital signature for the token.
1. **Token Verification**: When a recipient receives a JWT, they can verify its authenticity by using the corresponding public key. The public key is made available to anyone who needs to verify the JWT, typically through a public key infrastructure (PKI) or by exchanging keys securely.
1. **Asymmetric Encryption**: In the case of asymmetric encryption, the private key is used to sign the JWT during token generation, while the public key is used to verify the signature during token verification. This process ensures that the token was indeed issued by the expected party and has not been tampered with during transmission.
1. **Ensuring Security**: Using asymmetric encryption with public and private keys enhances the security of JWTs because the private key used for signing the token is kept confidential by the issuer and is never shared. The corresponding public key, which can be freely distributed, is used by recipients to verify the integrity and authenticity of the token.
1. **Key Management**: Proper key management practices are essential for the secure use of JWTs with public and private keys. This includes securely generating and storing private keys, securely distributing and managing public keys, and periodically rotating keys to mitigate security risks.


**How JSON Web Token is used multiple servers?**

Multiple servers but related or Microservices communicating to each other

