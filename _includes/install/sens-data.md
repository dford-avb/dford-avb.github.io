#### What is sensitive data? {#sens-data}

Openmage uses your encryption key to encrypt the following:

*	Credit card information
*	Usernames and passwords specified in the Openmage Admin configuration  (for example, logins to payment gateways)
*	CAPTCHA values sent over the network

Openmage does *not* encrypt:

*	Administrative and customer usernames and passwords (these passwords are hashed)
*	Address
*	Phone number
*	Other types of personally identifiable information except for credit card numbers
