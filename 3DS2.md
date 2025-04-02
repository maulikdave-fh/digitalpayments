# 3DS (3Domains Secure)
3 Domains - acquirer / merchants, issuers and card network

## Friction-less Transactions in 3DS 2.0
NO explicit 2FA a.k.a "Challenge"

### How is it possible?
#### Risk Based Authentication
Due to enriched data of 3DS2.x, issuers (their ACS) are able to make a call to "skip" the challenge and complete the authentication step.

Some of the data points used by ACS for risk based authentication;
##### Device / Browser Fingerprint
1. Every issuer / ACS has a <b><i>Method URL</i></b>, say a script (JS) that can collect browser / device info.
2. Card network "Directory Server" maintains the list of all <b><i>Method URLs</i></b> per issuer / ACS - BINs

  ```mermaid
  sequenceDiagram
  3DS Server->>Directory Server: Preparation Request (PREQ) to Director Server to collect issuer card ranges / ACS info
  Directory Server-->>3DS Server: Preparation Response (PRES) all info with Method URLs that 3DS server caches
  3DS Server ->> 3DS Client: At start of every transaction, 3DS Client receives the Method URL
  3DS Client ->> Directory Server: The JS at the Method URL is executed on the client browser to collect browser / device info
  ```

##### Past Transaction Behaviour
##### Transaction Amount


