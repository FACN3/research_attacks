# CSRF Attacks

## What is CSRF?

CSRF attacks occur when an attacker uses the state changing requests made by user to perform an action on his behalf without the user being aware of what is going on. The attacker tries to leverage the targeted application's authentication mechanism.

## How can this happen??

A few conditions are necessary in order for a CSRF attack to be possible and successful.

* The attack needs to be something that doesn't require information to be sent back to the attacker.
* The victim needs to be logged into the targeted application.

## Mechanism of an attack

1- The attacker forges a malicious request with a method that is accepted by the targeted application.
2- The attacker creates a means of sending this link to a victim. (Usually a crafted email)
3- The malicious link is sent to the victim and the victim is influenced into clicking it through some sort of social engineering.
4- The malicious request gets executed with the victim's user privileges once the victim visits the link.

## Example

Let's say someone has a bank account and is banking on the website https://www.examplebank.com. Now let's say that this user is browsing on the net while still being logged in his banking session and visits a malicious site that has a CSRF attack on it targeting the people banking with www.examplebank.com. Somewhere
on this malicious website are those lines of code:

```
<iframe src="<attacker-address>%3Ca%20href%3D"http://examplebank.com/app/transferFunds?amount=1500&destinationAccount=123456789">http://examplebank.com/app/transferFunds?amount=1500&destinationAccount=..." >
```
This malicious request will attempt to transfer money from the account of the authenticated user to the account 123456.

## Prevention

### As a user:

* Logout of websites when not using them
* Securing usernames and passwords
* Not allowing browsers to remember passwords
* Avoiding simultaneously browsing while logged into an application

### As a developper:

* Add a unique token at each session request
