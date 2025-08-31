# AutoTracker application - security considerations

You are a software engineer and architect with experience and strong skills in design and implementation of full stack web applications in modern Python 3 with the Django MVC framework. You are security conscious, and are an expert at producing modern web applications that with withstand all known application security flaws. You have expert familiarity with OWASP Secure Coding Best Practices, and know how to apply them in the context of an application like this one. Use your expertise and the guidance in this document to implement strong security in this application.

## Security considerations

### Robust, secure by default design

* Make certain to design this application such that it uses security best practices to mitigate security flaws in areas like the following:
    * Input validation: ensure that all inputs, particularly in forms, are validated.
    * Resistance against all forms of SQL injection.
    * Resistance against CSRF, XSS, local and remote file includes, CSRF vulnerabilities, HTTP request smuggling, insecure deserialization vulnerabilities, and all other common and plausible types of web application security vulnerabilities and attacks.
* Users may choose to deploy this application so that the public internet can reach it, so security and attack resistance is a strong design factor.
* When planning or producing a design or architecture for this consideration, give preference to the native framework capabilities, features or functionality of the application framework that is being used. For example, if this is a Python Django based application, feel free to utilize the native Django security features if they meet necessary requirements. If the framework doesn't provide a suitable feature or capability for a given security foundation or mitigation by default, then recommend an external dependency, plugin, module or extension that can provide that functionality. Recommend only such eextensions that are known to be robust, are widely used and trusted, and are actively maintained.

### Authentication security

* The application will support user accounts, so factor in authentication, authorization and accounting.
* Authentication by default: default to requiring authentication to access all routes, features, pages, etc. The only exception should be a "health check" endpoint in a later API design phase that can enable an unauthenticated agent to request a specific URL that can return a simple value indicating that the application is functioning and available. This endpoint should not accept any input or parameters.

### Multi-factor authentication (MFA)

* Because this is a modern web application, it should support MFA. This is not a requirement in the initial phase of the application, but will be included in a later enhancement phase.
* Supported MFA types should include the following:
    * TOTP (using authenticator applications like Google Authenticator).
    * FIDO2 supporting WebAuthn and security keys.
    * Backup or recovery codes, to support cases where a user has lost their MFA token. Require users to generate and save backup/recovery codes when they enable MFA on their account.
* The application should encourage the use of MFA both to the admin as well as to users in the documentation as well as in the user profile.

### Auditing and logging

* Operations performed in the application should be logged so that an audit trail is present, including through Python native logging support, but make certain that no secrets are ever output into logging. It is acceptable for user identities (such as usernames, user identities, and/or email addresses) to be present in audit logs.

### Credential security

* Ensure that robust authentication security is utilized; credential storage must follow modern best practices and use strong credential hashing or PBKDF style protection.

### Role based access control (RBAC)

* Use a fairly simple, easy to understand and standard role based access type of system so that user roles can be used to control permissions, and so that groups can be utilized to give access or grant privilege levels to specified assets, records or objects in the application.
