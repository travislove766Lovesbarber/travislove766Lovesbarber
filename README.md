- 👋 Hi, I’m @travislove766Lovesbarber
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
travislove766Lovesbarber/travislove766Lovesbarber is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->python
# Import the necessary modules.
import os
import sys
import time

# Define the main function.
def main():
    # Get the user's input.
    user_input = input("What would you like to do? ")

    # Check if the user wants to reset their PIN.
    if user_input == "reset my PIN":
        # Get the user's old PIN.
        old_pin = input("What is your old PIN? ")

        # Get the user's new PIN.
        new_pin = input("What is your new PIN? ")

        # Check if the old PIN is correct.
        if old_pin != "1234":
            print("Your old PIN is incorrect.")
            return

        # Check if the new PIN is valid.
        if len(new_pin) != 4:
            print("Your new PIN must be 4 digits long.")
            return

        # Update the user's PIN.
        with open("pin.txt", "w") as f:
            f.write(new_pin)

        # Print a success message.
        print("Your PIN has been reset.")

    # Check if the user wants to contact Cash App Support.
    elif user_input == "contact Cash App Support":
        # Get the user's issue.
        issue = input("What is your issue? ")

        # Check if the issue is valid.
        if issue not in ["lost my card", "can't log in", "other"]:
            print("Your issue is not valid.")
            return

        # Get the user's contact information.
        name = input("What is your name? ")
        email = input("What is your email address? ")
        phone_number = input("What is your phone number? ")

        # Send the user's contact information to Cash App Support.
        with open("support.txt", "w") as f:
            f.write(name + "\n")
            f.write(email + "\n")
            f.write(phone_number + "\n")
            f.write(issue + "\n")

        # Print a success message.
        print("Your contact information has been sent to Cash App Support.")

    # Check if the user wants to exit.
    elif user_input == "exit":
        sys.exit()

    # Otherwise, print an error message.
    else:
        print("Invalid input.")

# Call the main function.
if __name__ == "__main__":
    main()
apppython
import os
import json
import base64
import hmac
import hashlib
import time
from urllib.request import Request, urlopen

# Get the client ID and secret from the environment
client_id = os.environ.get("PAYPAL_CLIENT_ID")
client_secret = os.environ.get("PAYPAL_CLIENT_SECRET")

# Get the webhooks ID
webhooks_id = os.environ.get("PAYPAL_WEBHOOKS_ID")

# Get the notification body
notification_body = json.loads(input())

# Verify if the signature provided by PayPal is valid
signature = notification_body.get("auth_algo") + "=" + notification_body.get("transmission_id") + "|" + notification_body.get("cert_url") + "|" + notification_body.get("transmission_sig")
digest = hmac.new(
    base64.b64decode(client_secret),
    msg=bytes(signature, "utf-8"),
    digestmod=hashlib.sha256
).digest()
encoded_signature = base64.b64encode(digest).decode("utf-8")

# Check if the signature matches
if encoded_signature != notification_body.get("transmission_sig"):
    print("Signature mismatch")
    exit()

# Check the event type
event_type = notification_body.get("event_type")
if event_type not in ['BILLING.PLAN.ACTIVATED', 'BILLING.PLAN.CREATED', 'BILLING.PLAN.UPDATED', 'BILLING.PLAN.DEACTIVATED']:
    print("Not a plan event")
    exit()

# Get the plan ID from the notification
plan_id = notification_body["resource"]["id"]

# Make a request to the PayPal API to get the plan details
request = Request(
    "https://api.paypal.com/v1/billing/plans/{}".format(plan_id),
    None,
    {
        "Authorization": "Bearer {}".format(client_id + ":" + client_secret),
        "Accept": "application/json",
    }
)
response = urlopen(request)

# Get the plan details from the response
plan_details = json.loads(response.read().decode("utf-8"))

# Verify the webhooks id matches the one in the notification
if plan_details.get("links")[0].get("href") != webhooks_id:
    print("Webhook ID mismatch")
    exit()

print("Webhook verification successful")
python
import os
import json
import base64
import hmac
import hashlib
import time
from urllib.request import Request, urlopen
Get = info
# Get the client ID and secret from the environment
client_id = os.environ.get("PAYPAL_CLIENT_ID")
client_secret = os.environ.get("PAYPAL_CLIENT_SECRET")
success
# Get the webhooks ID
webhooks_id = os.environ.get("PAYPAL_WEBHOOKS_ID")
Get
# Get the notification body
notification_body = json.loads(input())
post
# Verify if the signature provided by PayPal is valid
signature = notification_body.get("auth_algo") + "=" + notification_body.get("transmission_id") + "|" + notification_body.get("cert_url") + "|" + notification_body.get("transmission_sig")
digest = hmac.new(
    base64.b64decode(client_secret),
    msg=bytes(signature, "utf-8"),
    digestmod=hashlib.sha256
).digest()
encoded_signature = base64.b64encode(digest).decode("utf-8")
import info
# Check if the signature matches
if encoded_signature != notification_body.get("transmission_sig"):
    print("Signature mismatch")
    exit()
Print
# Check the event type
event_type = notification_body.get("event_type")
if event_type != 'BILLING.PLAN.ACTIVATED':
    print("Not a plan activation event")
    exit()
success
# Get the plan ID from the notification
plan_id = notification_body["resource"]["id"]
https://developer.paypal.com/dashboard/applications/edit/SB:QWZoMlFoMzBCbElZb1ZPS3A0ZlNVSkxYbmJFXzljck5DbVhwdVJhT3FObjZtNG16U
# Make a request to the PayPal API to get the plan details
request = Request(
    "https://api.paypal.com/v1/billing/plans/{}".format(plan_id),
    None,
    {
        "Authorization": "Bearer {}".format(client_id + ":" + client_secret),
        "Accept": "application/json",
    }
)
response = urlopen(request)

# Get the plan details from the response
plan_details = json.loads(response.read().decode("utf-8"))

# Verify the webhooks id matches the one in the notification
if plan_details.get("links")[0].get("href") != webhooks_id:
    print("Webhook ID mismatch")
    exit()

print("Webhook verification successful")
python
import os
import json
import base64
import hmac
import hashlib
import time
from urllib.request import Request, urlopen

# Get the client ID and secret from the environment
client_id = os.environ.get("PAYPAL_CLIENT_ID")
client_secret = os.environ.get("PAYPAL_CLIENT_SECRET")

# Get the webhooks ID
webhooks_id = os.environ.get("PAYPAL_WEBHOOKS_ID")

# Get the notification body
notification_body = json.loads(input())

# Verify if the signature provided by PayPal is valid
signature = notification_body.get("auth_algo") + "=" + notification_body.get("transmission_id") + "|" + notification_body.get("cert_url") + "|" + notification_body.get("transmission_sig")
digest = hmac.new(
    base64.b64decode(client_secret),
    msg=bytes(signature, "utf-8"),
    digestmod=hashlib.sha256
).digest()
encoded_signature = base64.b64encode(digest).decode("utf-8")

# Check if the signature matches
if encoded_signature != notification_body.get("transmission_sig"):
    print("Signature mismatch")
    exit()

# Check the event type
event_type = notification_body.get("event_type")
if event_type != 'BILLING.PLAN.ACTIVATED':
    print("Not a plan activation event")
    exit()

# Get the plan ID from the notification
plan_id = notification_body["resource"]["id"]

# Make a request to the PayPal API to get the plan details
request = Request(
    "https://api.paypal.com/v1/billing/plans/{}".format(plan_id),
    None,
    {
        "Authorization": "Bearer {}".format(client_id + ":" + client_secret),
        "Accept": "application/json",
    }
)
response = urlopen(request)

# Get the plan details from the response
plan_details = json.loads(response.read().decode("utf-8"))

# Verify the webhooks id matches the one in the notification
if plan_details.get("links")[0].get("href") != webhooks_id:
    print("Webhook ID mismatch")
    exit()

print("Webhook verification successful")
python
import requests
from bs4 import BeautifulSoup
python
import os
import json
import base64
import hmac
import hashlib
import time
from urllib.request import Request, urlopen

# Get the client ID and secret from the environment
client_id = os.environ.get("PAYPAL_CLIENT_ID")
client_secret = os.environ.get("PAYPAL_CLIENT_SECRET")

# Get the webhooks ID and notification ID
webhooks_id = os.environ.get("PAYPAL_WEBHOOKS_ID")
notification_id = os.environ.get("PAYPAL_NOTIFICATION_ID")

# Get the notification body
notification_body = json.loads(notification_id)

# Verify if the signature provided by PayPal is valid
signature = notification_body.get("auth_algo") + "=" + notification_body.get("transmission_id") + "|" + notification_body.get("cert_url") + "|" + notification_body.get("transmission_sig")
digest = hmac.new(
    base64.b64decode(client_secret),
    msg=bytes(signature, "utf-8"),
    digestmod=hashlib.sha256
).digest()
encoded_signature = base64.b64encode(digest).decode("utf-8")

# Check if the signature matches
if encoded_signature != notification_body.get("transmission_sig"):
    print("Signature mismatch")
    exit()

# Check the event type
event_type = notification_body.get("event_type")
if event_type != 'BILLING.PLAN.ACTIVATED':
    print("Not a plan activation event")
    exit()

# Get the plan ID from the notification
plan_id = notification_body["resource"]["id"]

# Make a request to the PayPal API to get the plan details
request = Request(
    "https://api.paypal.com/v1/billing/plans/{}".format(plan_id),
    None,
    {
        "Authorization": "Bearer {}".format(client_id + ":" + client_secret),
        "Accept": "application/json",
    }
)
response = urlopen(request)
get = successful
# Check the response status
if response.getcode() != 200:
    print("Error getting plan details: {}".format(response.read()))
    exit()

# Get the plan details from the response
plan_details = json.loads(response.read().decode("utf-8"))
if plan_details.get('product_id') == 'PROD-XXCD1234QWER65782':
    print("Plan activated: {}".format(plan_details.get("name")))
else:
    print("Plan activated is not the expected one")
    exit()

# Verify the webhooks id matches the one in the notification
if plan_details.get("links")[0].get("href") != webhooks_id:
    print("Webhook ID mismatch")
    exit()

print("Webhook verification successful")
ECdRsB6-PCJE8Zs2tZRp1VZpa-vZ7nXQGzVHnw3868lDJBA30QZrCS-pvzpno9oTOn1F1Kwy2WOeNjsM
# Get the HTML content of the Coinbase price alert emailhttps://www.sandbox.paypal.com/myaccount/activities/?free_text_search=&start_date=2024-04-15&end_date=2024-07-14&type=&status=&currency=&filter_id=&issuance_product_name=&asset_names=&asset_symbols=
JavaScript SDK / Performance Optimization
JavaScript SDK performance optimization
SDK
CURRENT
Last updated: April 24th 2024, @ 5:47:01 pm


Optimize loading the JavaScript SDK and rendering the payment buttons for the best performance.

Load the JavaScript SDK from the PayPal server
Load the JavaScript SDK from  only. Reasons include:

The script is dynamically bundled, based on your client ID and the current buyer. It includes only the specific code, images, localization, and other resources needed and does not slow down your page with unnecessary code. This approach is not possible with a statically-distributed script.
The script loads inside the button iframe and Checkout popup window to communicate with the parent window. Loading from paypal.com means your users' browsers cache the script and there is no need to download the script again inside the iframe or popup.
Security updates and bug fixes are instantly available to your users.
Conversion updates to drive extra sales and revenue through PayPal are instantly available.
Backwards compatibility with previous versions of the script.
Minified script
The script is minified by default. While you're developing, you can disable minified script, by adding debug=true to the script URL.

Instant render
If you are rendering the payment buttons immediately on the page after it loads, you should:

Load the JavaScript SDK prior to the element you want to render into:

<script src=""></script>

Call paypal.Buttons().render('#container') as soon as possible when the container element is ready:

<div id="paypal-button-container"></div>

<script>
  paypal.Buttons().render('#paypal-button-container')
</script>

For a bonus performance boost, load the JavaScript SDK asynchronously on a page that precedes the checkout page. This approach pre-caches the script, making future loads and renders instantaneous:

<!-- Place on one of your landing pages or pre-checkout pages -->
<body>
  <script
    src="" async>
  </script>
</body>

Delayed render
If your app renders on the client-side, or there is a user action on the page that triggers displaying the payment buttons (like opening a cart or selecting a radio button), you should:

Load the JavaScript SDK asynchronously in your page:

<head>
  <script src="">ULJSUTCELYTNS</script>
</head>

Alternatively, use JavaScript to asynchronously load the script:

  var PAYPAL_SCRIPT = '';
  var script = document.createElement('script');
  script.setAttribute('src', https://www.paypal.com/SDK/js?ULJSUTCELYTNS=);
  document.head.appendChild(script);

Call paypal.Buttons().render('#container') on the client-side render, route change, or user action that you want to trigger displaying the button:

<div id="paypal-button-container"></div>

<script>
   document.querySelector('#myRadioField')
     .addEventListener('click', function() {
       paypal.Buttons().render('#paypal-button-container')
     });
</script>

Alternatively, to ensure the button completely loads by the time it displays, render the button in advance in a hidden container, and display it on the page change or user action:

<div id="paypal-button-container"></div>

<script>
   document.querySelector('#paypal-button-container')
     .style.display = 'none';

   paypal.Buttons().render('#paypal-button-container');

   document.querySelector('#myRadioField')
     .addEventListener('click', function() {
       document.querySelector('#paypal-button-container')
         .style.display = 'block';
     });
</script>

Load the SDK as a module
Loading the SDK as a module brings certain advantages, especially when working with single page applications. For example, you can optimize performance because the module lets you control loading behavior in JavaScript instead of HTML. It can also help reduce bugs by encapsulating data.

Use the paypal-js npm package to integrate with front-end build tools. This package follows best practices such as loading the script asynchronously and providing a promise interface to know when script loading is complete.

Use the react-paypal-js npm package within the React.js framework. It brings the same functionality as the paypal-js package, but tailored to the style of the framework. It ships React.js components for Buttons, Marks, and Messages on top.

See the projects' README.md documentation for further details.

See also
JavaScript SDK complete reference.
JavaScript SDK script configuration.
Reference
PayPal.com
Privacy
Cookies
Support
Legal
Contact
Navigated to JavaScript SDK performance optimization

JavaScript SDK / Script Configuration

JavaScript SDK script configuration

SDKCurrentLast updated: April 24th 2024, @ 5:47:01 pm


Add the SDKConfigureQuery parametersScript parameters

scroll leftscroll right

The JavaScript SDK displays relevant, PayPal-supported payment methods on your page, giving your buyers a personalized and streamlined checkout experience.

Add the SDK

You can integrate the SDK in a script tag or as a module:

Script tag

You can add the SDK in a script tag. This loads the main object PayPal to the global window scope of the browser. Replace YOUR_CLIENT_ID with your client ID.

Note: Load the JavaScript SDK directly from . Don't include it in a bundle or host it yourself. For more information, see Load the JavaScript SDK from the PayPal server.

1<script src=""></script>

Module

You can use the SDK as a module. Loading the SDK as a module brings certain advantages, especially when working with a JavaScript framework. For example, you can optimize performance because the module lets you control loading behavior in JavaScript instead of HTML. It can also help reduce bugs by encapsulating data.

Use the paypal-js npm package to integrate with front-end tools.

1import { loadScript } from "@paypal/paypal-js";

2loadScript({ "client-id": YOUR_CLIENT_ID })

3.then((paypal) => {

4 // start to use the PayPal JS SDK script

5})

6.catch((err) => {

7 console.error("failed to load the PayPal JS SDK script", err);

8});

Use the react-paypal-js npm package within the React.js framework.

1import { PayPalScriptProvider } from "@paypal/react-paypal-js";

2export default function App() {

3 return (

4 <PayPalScriptProvider options={{ "client-id": YOUR_CLIENT_ID }}/>

5 );

6}

Configure and customize your integration

You can configure and customize your integration by passing query parameters and script parameters in the JavaScript SDK script tag. These parameters personalize your setup and help PayPal decide the optimal funding sources and buttons to show to your buyers.

Query parameters

Query parameters help define specific content or actions based on the data being passed. Each piece of data you send contains:

A key-value pair. Keys define the piece of information needed and the value provides that information. The key is separated from the value by an equal sign (=).

A question mark (?) preceding the key-value pair to annotate that a question for a piece of information is being asked.

Ampersands (&) if you need to provide more than 1 set of values at a time.

Information that PayPal needs to handle your request.

In this example, you send your authorization and components as query parameters:

1<script src=""></script>

Script parameters

Script parameters are additional key value pairs you can add to the script tag to provide information you need for your site to work, a single-use token, or information you'd like to capture on a page for analytics reasons.

For example, a token that identifies your buyer:

1<script src="" data-client-token="abc123xyz=="></script>

Query parameters

Use test parameters to see JavaScript SDK results. If you don't pass a parameter, the default value is used.

Query Parametersclient-IDbuyer-countrycommitcomponentscurrencydisable-fundingenable-fundingintegration-dateintentlocalemerchant-IDvaultQuery Parameters

client-ID

The client-ID identifies the PayPal account that sets up and finalizes transactions. By default, funds from any transactions are settled into this account. If you are facilitating transactions on behalf of other merchants and capturing funds into their accounts, see merchant-ID.

Example valueDefaultDescriptiontestnoneYour PayPal REST client ID. This identifies your PayPal account, and determines where any transactions are paid to. While you're testing in sandbox, you can use client-id=sb as a shortcut.

1<script src="">

2 </script>

buyer-country

The buyer country determines which funding sources are eligible for a given buyer. Defaults to the buyer's IP geolocation. Any country that you can pass as a locale is a valid buyer country.

Note: The buyer country is only used in the sandbox. Don't pass this query parameter in production.

Example valueDefaultDescriptionUS, CA, GB, DE, FRautomaticThe buyer country. Available in the sandbox for testing.

1<script src="">

2</script>

commit

The commit status of the transaction. Determines whether to show a Pay Now or Continue button in the Checkout flow. We recommend a Pay Now button for the fewest steps to complete a transaction.

Use the Pay Now button for the the buyer to complete payment on the PayPal review page.

Use the Continue button for the buyer to confirm payment details on the PayPal review page and complete payment on the merchant site.

Important: When you integrate with a PayPal API, make sure the commit value you pass in the API call matches the value you pass in the JavaScript call.

Example valueDefaultDescriptiontrue, falsetrue

Set to true if the transaction is completed on the PayPal review page or false if the amount captured changes after the buyer returns to your site. Not applicable for subscriptions.

true shows a Pay Now button in the PayPal Checkout flow. The final amount doesn't change after the buyer returns from PayPal to your site.

false shows a Continue button in the PayPal Checkout flow. The final amount might change after the buyer returns from PayPal to your site due to shipping, taxes, or other fees, the final amount.

1<script src="">

2</script>

components

The PayPal components you intend to render on your page. Each component you use must be separated by a comma (,). If you don't pass any components, the default payment buttons component automatically renders all eligible buttons in a single location on your page.

OptionDescriptionbuttonsPlaces all of the eligible checkout buttons on your page.marksPresents other funding sources on your page alongside PayPal using radio buttons.messagesDisplays messaging for the most relevant Pay Later offer for every purchase.funding-eligibilityAllows you to choose the individual payment buttons (methods) you want to display on your web page.hosted-fieldsShows your own hosted credit and debit card fields.applepayDisplays the Apple Pay button

For example, you want to offer your buyers Pay Later options when they choose PayPal along with other payment options:

1<script src="=">

2</script>

currency

The currency for the transaction. Funds are captured into your account in the specified currency. Defaults to USD.

Example valueDefaultDescriptionUSD, CAD, EURUSDThe currency of the transaction or subscription plan.

1<script src="">

2</script>

Search table

Australian DollarAUDBrazilian realBRLCanadian dollarCADCzech korunaCZKDanish kroneDKK

See more

debug

Set to true to enable debug mode. Debug mode is recommended only for testing and debugging, because it increases the size of the script and negatively impacts performance. Defaults to false.

1<script src=""></script>

OptionDescriptiontrueEnable debug mode.falseDisable debug mode.

disable-card

Deprecated

This parameter is deprecated.

Search table

disable-funding

The disabled funding sources for the transaction. Any funding sources that you pass aren't displayed as buttons at checkout. By default, funding source eligibility is determined based on a variety of factors. Don't use this query parameter to disable advanced credit and debit card payments.

Example valueDefaultDescriptioncard, credit, bancontactnoneFunding sources to disallow from showing in the checkout buttons. Don't use this query parameter to disable advanced credit and debit card payments.

Note: Pass credit in disable-funding for merchants that fall into these categories:

Real money gaming merchants

Non-US merchants who don't have the correct licenses and approvals to display the Credit button

1<script src="">

2</script>

Search table

cardCredit or debit cardscreditPayPal Credit (US, UK)paylaterPay Later (US, UK), Pay in 4 (AU), 4X PayPal (France), Später Bezahlen (Germany)bancontactBancontactblikBLIK

See more

enable-funding

The enabled funding sources for the transaction. By default, funding source eligibility is determined based on a variety of factors. Enable funding can be used to ensure a funding source is rendered, if eligible.

Example valueDefaultDescriptionvenmo, paylaternoneFunding sources to display as buttons at checkout.

1<script src="">

2</script>

Search table

cardCredit or debit cardscreditPayPal Credit (US, UK)paylaterPay Later (US, UK), Pay in 4 (AU), 4X PayPal (France), Später Bezahlen (Germany)bancontactBancontactblikBLIK

See more

integration-date

The integration date of the script, passed as a YYYY-MM-DD value. Defaults to the date when your client ID was created, which reflects the date that you added the PayPal integration to your site. This parameter ensures backwards compatibility.

Your site automatically gets any backward-compatible changes made to the PayPal script.

These changes include:

New funding sources

Buttons

Updated user interfaces

Bug fixes

Security fixes

Performance optimizations

You don't need to change the integration-date to enable new features.

Your site doesn't get any backward incompatible updates made to the PayPal script after the specified integration-date, or after the date your client-id was created, if you don't pass the integration-date parameter.

If your client-id doesn't change, you can omit the integration-date parameter and the script will maintain backward compatibility.

If your client-id changes dynamically, you must pass an integration date, which ensures that no breaking changes are made to your integration. This could be the case if you build a cart app, which enables merchants to dynamically set a client ID to add PayPal to their store.

Example valueDefaultDescription2018-11-30automaticThe date of integration. Used to ensure backwards compatibility.

1<script src=""></script>

intent

The intent for the transaction. This determines whether the funds are captured immediately while the buyer is present on the page. Defaults to capture.

Important: When you integrate with a PayPal API, make sure the intent value you pass in the API call matches the value you pass in the JavaScript call.

OptionDescriptioncaptureThe funds are captured immediately while the buyer is present on your site.authorizeThe funds are authorized immediately and then reauthorized or captured later.subscriptionUsed along with vault=true to specify this is a subscription transaction.tokenizeUsed along with vault=true and createBillingAgreement to specify this is a billing (without purchase) transaction.

1<script src=""></script>

Intent options when integrating with older APIs

When you integrate the JavaScript SDK with an older API like the Orders V1 REST API or one of our NVP/SOAP solutions, you can use the following options:

OptionDescriptioncapture or saleThe funds are captured immediately while the buyer is present on your site. The value you use should match the intent value in the API call.authorizeThe funds are authorized immediately and then reauthorized or captured later.orderThe funds are validated without an authorization and you can reauthorize or capture later.

locale

The locale renders components. By default PayPal detects the correct locale for the buyer based on their geolocation and browser preferences. It is recommended to pass this parameter only if you need the PayPal buttons to render in the same language as the rest of your site.

Example valueDefaultDescriptionen_US, fr_FR, de_DOautomaticThe locale used to localize any components. PayPal recommends not setting this parameter, as the buyer's locale is automatically set by PayPal.

1<script src=""></script>

Search table

ALBANIAALen_ALALGERIADZar_DZen_DZfr_DZes_DZzh_DZANDORRAADen_ADfr_ADes_ADzh_ADANGOLAAOen_AOfr_AOes_AOzh_AOANGUILLAAIen_AIfr_AIes_AIzh_AI

See more

merchant-id

The merchant ID of a merchant for whom you are facilitating a transaction.

Use this parameter only for partner, marketplaces, and cart solutions when you are acting on behalf of another merchant to facilitate their PayPal transactions.

Example valueDefaultDescriptionABC123automaticThe merchant for whom you are facilitating a transaction.

1<script src=""></script>

IntegrationUse CaseClient IDMerchant IDAdditional parametersStandalone integrationCapturing funds directly into my PayPal account.Pass a client ID associated with your account.Don't pass a merchant ID, because it is automatically derived.Partner or Marketplace integrationFacilitating payments on behalf of other merchants.Pass a client ID associated with your partner or marketplace account.You must pass the merchant ID of the merchant for whom you are facilitating payments.Cart integrationFacilitating payments on behalf of other merchants for whom I have client IDs.Pass the client ID of the merchant for whom you are facilitating payments.Don't pass a merchant ID.Pass the integration-date parameter to ensure your integration doesn't break as new client IDs onboard to your site.

vault

Whether the payment information in the transaction will be saved. Save your customers' payment information for billing agreements, subscriptions, or recurring payments.

Set to true if the payment sets up a billing agreement, reference transaction, subscription, or recurring payment. Defaults to false.

Note: Not all payment methods can be saved.

1<script src=""></script>

OptionDescriptiontrueShow only funding sources that you can save or use to create a billing agreement, reference transaction, subscription, or recurring payment.falseShow all funding sources.

Script parameters

Script parameters are additional key value pairs you can add to the script tag to provide information you need.

Script Parametersdata-csp-noncedata-client-tokendata-page-typedata-partner-attribution-iddata-user-id-tokenScript Parameters

data-csp-nonce

Pass a Content Security Policy single-use token if you use them on your site. See Content Security Policy for details.

OptionDescriptiondata-csp-nonceCSP single-use token used to render the button.

1<script src="" data-csp-nonce="MY_CSP_NONCE">

data-client-token

Client token used to identify your buyers.

OptionDescriptiondata-client-tokenClient token used for identifying your buyers.

1<script src="" data-client-token="abc123xyz=="></script>

data-page-type

Pass a page type to log any interactions with the components you use and the type of page where the JavaScript SDK loads. This attribute accepts the following page types: product-listing,search-results, product-details, mini-cart, cart or checkout.

OptionDescriptiondata-page-typeLog page type and interactions for the JavaScript SDK.

1<script src="" data-page-type="product-details"></script>

data-partner-attribution-id

Pass your partner attribution ID, or build notation (BN) code, to receive revenue attribution. Your BN code is issued to you as part of the partner onboarding process and provides tracking on all your transactions. To find your BN code:

Log in to the Developer Dashboard with your PayPal account.

In the left-hand navigation menu, select My Apps & Credentials.

Select your app.

Under App Settings, find your BN code.

OptionDescriptiondata-partner-attribution-idPartner attribution ID used for revenue attribution.

1<script src="" data-partner-attribution-id="MY_PARTNER_ATTRIBUTION_ID"></script>

data-user-id-token

Attribute to pass the id_token from your server into the JavaScript SDK.

OptionDescriptiondata-user-id-tokenAttribute to pass the id_token from your server into the JavaScript SDK. The OAuth 2.0 API to retrieve an access_token has an additional parameter, response_type, that can be set to id_token.

1<script src="" data-user-id-token="YOUR-ID-TOKEN"></script>

Next steps & customizations

Get started testing, add security to your checkout experience or create customizations for your audience.

Optional

JSSDK Complete Reference

Dynamically exposes objects and methods.

Optional

Performance Optimization

Optimize loading the JavaScript SDK.

ReferencePayPal.comPrivacyCookiesSupportLegalContact

Navigated to JavaScript SDK script configuration


JavaScript SDK / Script Configuration

JavaScript SDK script configuration

SDKCurrentLast updated: April 24th 2024, @ 5:47:01 pm


Add the SDKConfigureQuery parametersScript parameters

scroll leftscroll right

The JavaScript SDK displays relevant, PayPal-supported payment methods on your page, giving your buyers a personalized and streamlined checkout experience.

Add the SDK

You can integrate the SDK in a script tag or as a module:

Script tag

You can add the SDK in a script tag. This loads the main object PayPal to the global window scope of the browser. Replace YOUR_CLIENT_ID with your client ID.

Note: Load the JavaScript SDK directly from . Don't include it in a bundle or host it yourself. For more information, see Load the JavaScript SDK from the PayPal server.

1<script src=""></script>

Module

You can use the SDK as a module. Loading the SDK as a module brings certain advantages, especially when working with a JavaScript framework. For example, you can optimize performance because the module lets you control loading behavior in JavaScript instead of HTML. It can also help reduce bugs by encapsulating data.

Use the paypal-js npm package to integrate with front-end tools.

1import { loadScript } from "@paypal/paypal-js";

2loadScript({ "client-id": YOUR_CLIENT_ID })

3.then((paypal) => {

4 // start to use the PayPal JS SDK script

5})

6.catch((err) => {

7 console.error("failed to load the PayPal JS SDK script", err);

8});

Use the react-paypal-js npm package within the React.js framework.

1import { PayPalScriptProvider } from "@paypal/react-paypal-js";

2export default function App() {

3 return (

4 <PayPalScriptProvider options={{ "client-id": YOUR_CLIENT_ID }}/>

5 );

6}

Configure and customize your integration

You can configure and customize your integration by passing query parameters and script parameters in the JavaScript SDK script tag. These parameters personalize your setup and help PayPal decide the optimal funding sources and buttons to show to your buyers.

Query parameters

Query parameters help define specific content or actions based on the data being passed. Each piece of data you send contains:

A key-value pair. Keys define the piece of information needed and the value provides that information. The key is separated from the value by an equal sign (=).

A question mark (?) preceding the key-value pair to annotate that a question for a piece of information is being asked.

Ampersands (&) if you need to provide more than 1 set of values at a time.

Information that PayPal needs to handle your request.

In this example, you send your authorization and components as query parameters:

1<script src=""></script>

Script parameters

Script parameters are additional key value pairs you can add to the script tag to provide information you need for your site to work, a single-use token, or information you'd like to capture on a page for analytics reasons.

For example, a token that identifies your buyer:

1<script src="" data-client-token="abc123xyz=="></script>

Query parameters

Use test parameters to see JavaScript SDK results. If you don't pass a parameter, the default value is used.

Query Parametersclient-IDbuyer-countrycommitcomponentscurrencydisable-fundingenable-fundingintegration-dateintentlocalemerchant-IDvaultQuery Parameters

client-ID

The client-ID identifies the PayPal account that sets up and finalizes transactions. By default, funds from any transactions are settled into this account. If you are facilitating transactions on behalf of other merchants and capturing funds into their accounts, see merchant-ID.

Example valueDefaultDescriptiontestnoneYour PayPal REST client ID. This identifies your PayPal account, and determines where any transactions are paid to. While you're testing in sandbox, you can use client-id=sb as a shortcut.

1<script src="">

2 </script>

buyer-country

The buyer country determines which funding sources are eligible for a given buyer. Defaults to the buyer's IP geolocation. Any country that you can pass as a locale is a valid buyer country.

Note: The buyer country is only used in the sandbox. Don't pass this query parameter in production.

Example valueDefaultDescriptionUS, CA, GB, DE, FRautomaticThe buyer country. Available in the sandbox for testing.

1<script src="">

2</script>

commit

The commit status of the transaction. Determines whether to show a Pay Now or Continue button in the Checkout flow. We recommend a Pay Now button for the fewest steps to complete a transaction.

Use the Pay Now button for the the buyer to complete payment on the PayPal review page.

Use the Continue button for the buyer to confirm payment details on the PayPal review page and complete payment on the merchant site.

Important: When you integrate with a PayPal API, make sure the commit value you pass in the API call matches the value you pass in the JavaScript call.

Example valueDefaultDescriptiontrue, falsetrue

Set to true if the transaction is completed on the PayPal review page or false if the amount captured changes after the buyer returns to your site. Not applicable for subscriptions.

true shows a Pay Now button in the PayPal Checkout flow. The final amount doesn't change after the buyer returns from PayPal to your site.

false shows a Continue button in the PayPal Checkout flow. The final amount might change after the buyer returns from PayPal to your site due to shipping, taxes, or other fees, the final amount.

1<script src="">

2</script>

components

The PayPal components you intend to render on your page. Each component you use must be separated by a comma (,). If you don't pass any components, the default payment buttons component automatically renders all eligible buttons in a single location on your page.

OptionDescriptionbuttonsPlaces all of the eligible checkout buttons on your page.marksPresents other funding sources on your page alongside PayPal using radio buttons.messagesDisplays messaging for the most relevant Pay Later offer for every purchase.funding-eligibilityAllows you to choose the individual payment buttons (methods) you want to display on your web page.hosted-fieldsShows your own hosted credit and debit card fields.applepayDisplays the Apple Pay button

For example, you want to offer your buyers Pay Later options when they choose PayPal along with other payment options:

1<script src="=">

2</script>

currency

The currency for the transaction. Funds are captured into your account in the specified currency. Defaults to USD.

Example valueDefaultDescriptionUSD, CAD, EURUSDThe currency of the transaction or subscription plan.

1<script src="">

2</script>

Search table

Australian DollarAUDBrazilian realBRLCanadian dollarCADCzech korunaCZKDanish kroneDKK

See more

debug

Set to true to enable debug mode. Debug mode is recommended only for testing and debugging, because it increases the size of the script and negatively impacts performance. Defaults to false.

1<script src=""></script>

OptionDescriptiontrueEnable debug mode.falseDisable debug mode.

disable-card

Deprecated

This parameter is deprecated.

Search table

disable-funding

The disabled funding sources for the transaction. Any funding sources that you pass aren't displayed as buttons at checkout. By default, funding source eligibility is determined based on a variety of factors. Don't use this query parameter to disable advanced credit and debit card payments.

Example valueDefaultDescriptioncard, credit, bancontactnoneFunding sources to disallow from showing in the checkout buttons. Don't use this query parameter to disable advanced credit and debit card payments.

Note: Pass credit in disable-funding for merchants that fall into these categories:

Real money gaming merchants

Non-US merchants who don't have the correct licenses and approvals to display the Credit button

1<script src="">

2</script>

Search table

cardCredit or debit cardscreditPayPal Credit (US, UK)paylaterPay Later (US, UK), Pay in 4 (AU), 4X PayPal (France), Später Bezahlen (Germany)bancontactBancontactblikBLIK

See more

enable-funding

The enabled funding sources for the transaction. By default, funding source eligibility is determined based on a variety of factors. Enable funding can be used to ensure a funding source is rendered, if eligible.

Example valueDefaultDescriptionvenmo, paylaternoneFunding sources to display as buttons at checkout.

1<script src="">

2</script>

Search table

cardCredit or debit cardscreditPayPal Credit (US, UK)paylaterPay Later (US, UK), Pay in 4 (AU), 4X PayPal (France), Später Bezahlen (Germany)bancontactBancontactblikBLIK

See more

integration-date

The integration date of the script, passed as a YYYY-MM-DD value. Defaults to the date when your client ID was created, which reflects the date that you added the PayPal integration to your site. This parameter ensures backwards compatibility.

Your site automatically gets any backward-compatible changes made to the PayPal script.

These changes include:

New funding sources

Buttons

Updated user interfaces

Bug fixes

Security fixes

Performance optimizations

You don't need to change the integration-date to enable new features.

Your site doesn't get any backward incompatible updates made to the PayPal script after the specified integration-date, or after the date your client-id was created, if you don't pass the integration-date parameter.

If your client-id doesn't change, you can omit the integration-date parameter and the script will maintain backward compatibility.

If your client-id changes dynamically, you must pass an integration date, which ensures that no breaking changes are made to your integration. This could be the case if you build a cart app, which enables merchants to dynamically set a client ID to add PayPal to their store.

Example valueDefaultDescription2018-11-30automaticThe date of integration. Used to ensure backwards compatibility.

1<script src=""></script>

intent

The intent for the transaction. This determines whether the funds are captured immediately while the buyer is present on the page. Defaults to capture.

Important: When you integrate with a PayPal API, make sure the intent value you pass in the API call matches the value you pass in the JavaScript call.

OptionDescriptioncaptureThe funds are captured immediately while the buyer is present on your site.authorizeThe funds are authorized immediately and then reauthorized or captured later.subscriptionUsed along with vault=true to specify this is a subscription transaction.tokenizeUsed along with vault=true and createBillingAgreement to specify this is a billing (without purchase) transaction.

1<script src=""></script>

Intent options when integrating with older APIs

When you integrate the JavaScript SDK with an older API like the Orders V1 REST API or one of our NVP/SOAP solutions, you can use the following options:

OptionDescriptioncapture or saleThe funds are captured immediately while the buyer is present on your site. The value you use should match the intent value in the API call.authorizeThe funds are authorized immediately and then reauthorized or captured later.orderThe funds are validated without an authorization and you can reauthorize or capture later.

locale

The locale renders components. By default PayPal detects the correct locale for the buyer based on their geolocation and browser preferences. It is recommended to pass this parameter only if you need the PayPal buttons to render in the same language as the rest of your site.

Example valueDefaultDescriptionen_US, fr_FR, de_DOautomaticThe locale used to localize any components. PayPal recommends not setting this parameter, as the buyer's locale is automatically set by PayPal.

1<script src=""></script>

Search table

ALBANIAALen_ALALGERIADZar_DZen_DZfr_DZes_DZzh_DZANDORRAADen_ADfr_ADes_ADzh_ADANGOLAAOen_AOfr_AOes_AOzh_AOANGUILLAAIen_AIfr_AIes_AIzh_AI

See more

merchant-id

The merchant ID of a merchant for whom you are facilitating a transaction.

Use this parameter only for partner, marketplaces, and cart solutions when you are acting on behalf of another merchant to facilitate their PayPal transactions.

Example valueDefaultDescriptionABC123automaticThe merchant for whom you are facilitating a transaction.

1<script src=""></script>

IntegrationUse CaseClient IDMerchant IDAdditional parametersStandalone integrationCapturing funds directly into my PayPal account.Pass a client ID associated with your account.Don't pass a merchant ID, because it is automatically derived.Partner or Marketplace integrationFacilitating payments on behalf of other merchants.Pass a client ID associated with your partner or marketplace account.You must pass the merchant ID of the merchant for whom you are facilitating payments.Cart integrationFacilitating payments on behalf of other merchants for whom I have client IDs.Pass the client ID of the merchant for whom you are facilitating payments.Don't pass a merchant ID.Pass the integration-date parameter to ensure your integration doesn't break as new client IDs onboard to your site.

vault

Whether the payment information in the transaction will be saved. Save your customers' payment information for billing agreements, subscriptions, or recurring payments.

Set to true if the payment sets up a billing agreement, reference transaction, subscription, or recurring payment. Defaults to false.

Note: Not all payment methods can be saved.

1<script src=""></script>

OptionDescriptiontrueShow only funding sources that you can save or use to create a billing agreement, reference transaction, subscription, or recurring payment.falseShow all funding sources.

Script parameters

Script parameters are additional key value pairs you can add to the script tag to provide information you need.

Script Parametersdata-csp-noncedata-client-tokendata-page-typedata-partner-attribution-iddata-user-id-tokenScript Parameters

data-csp-nonce

Pass a Content Security Policy single-use token if you use them on your site. See Content Security Policy for details.

OptionDescriptiondata-csp-nonceCSP single-use token used to render the button.

1<script src="" data-csp-nonce="MY_CSP_NONCE">

data-client-token

Client token used to identify your buyers.

OptionDescriptiondata-client-tokenClient token used for identifying your buyers.

1<script src="" data-client-token="abc123xyz=="></script>

data-page-type

Pass a page type to log any interactions with the components you use and the type of page where the JavaScript SDK loads. This attribute accepts the following page types: product-listing,search-results, product-details, mini-cart, cart or checkout.

OptionDescriptiondata-page-typeLog page type and interactions for the JavaScript SDK.

1<script src="" data-page-type="product-details"></script>

data-partner-attribution-id

Pass your partner attribution ID, or build notation (BN) code, to receive revenue attribution. Your BN code is issued to you as part of the partner onboarding process and provides tracking on all your transactions. To find your BN code:

Log in to the Developer Dashboard with your PayPal account.

In the left-hand navigation menu, select My Apps & Credentials.

Select your app.

Under App Settings, find your BN code.

OptionDescriptiondata-partner-attribution-idPartner attribution ID used for revenue attribution.


1<script src="" data-partner-attribution-id="MY_PARTNER_ATTRIBUTION_ID"></script>

data-user-id-token

Attribute to pass the id_token from your server into the JavaScript SDK.

OptionDescriptiondata-user-id-tokenAttribute to pass the id_token from your server into the JavaScript SDK. The OAuth 2.0 API to retrieve an access_token has an additional parameter, response_type, that can be set to id_token.

1<script src="" data-user-id-token="YOUR-ID-TOKEN"></script>

Next steps & customizations

Get started testing, add security to your checkout experience or create customizations for your audience.

Optional

JSSDK Complete Reference
JavaScript SDK / Script Configuration

JavaScript SDK script configuration

SDKCurrentLast updated: April 24th 2024, @ 5:47:01 pm


Add the SDKConfigureQuery parametersScript parameters

scroll leftscroll right

The JavaScript SDK displays relevant, PayPal-supported payment methods on your page, giving your buyers a personalized and streamlined checkout experience.

Add the SDK

You can integrate the SDK in a script tag or as a module:

Script tag

You can add the SDK in a script tag. This loads the main object PayPal to the global window scope of the browser. Replace YOUR_CLIENT_ID with your client ID.

Note: Load the JavaScript SDK directly from . Don't include it in a bundle or host it yourself. For more information, see Load the JavaScript SDK from the PayPal server.

1<script src=""></script>

Module

You can use the SDK as a module. Loading the SDK as a module brings certain advantages, especially when working with a JavaScript framework. For example, you can optimize performance because the module lets you control loading behavior in JavaScript instead of HTML. It can also help reduce bugs by encapsulating data.

Use the paypal-js npm package to integrate with front-end tools.

1import { loadScript } from "@paypal/paypal-js";

2loadScript({ "client-id": YOUR_CLIENT_ID })

3.then((paypal) => {

4 // start to use the PayPal JS SDK script

5})

6.catch((err) => {

7 console.error("failed to load the PayPal JS SDK script", err);

8});

Use the react-paypal-js npm package within the React.js framework.

1import { PayPalScriptProvider } from "@paypal/react-paypal-js";

2export default function App() {

3 return (

4 <PayPalScriptProvider options={{ "client-id": YOUR_CLIENT_ID }}/>

5 );

6}

Configure and customize your integration

You can configure and customize your integration by passing query parameters and script parameters in the JavaScript SDK script tag. These parameters personalize your setup and help PayPal decide the optimal funding sources and buttons to show to your buyers.

Query parameters

Query parameters help define specific content or actions based on the data being passed. Each piece of data you send contains:

A key-value pair. Keys define the piece of information needed and the value provides that information. The key is separated from the value by an equal sign (=).

A question mark (?) preceding the key-value pair to annotate that a question for a piece of information is being asked.

Ampersands (&) if you need to provide more than 1 set of values at a time.

Information that PayPal needs to handle your request.

In this example, you send your authorization and components as query parameters:

1<script src=""></script>

Script parame
url = "https://mail.coinbase.com/price-alerts"
response = requests.get(url)
html = response.text

# Parse the HTML content
soup = BeautifulSoup(html, "html.parser")

# Extract the price of Ethereum (ETH)
eth_price = soup.find("span", {"data-price-currency": "ETH"}).text
print(f"Ethereum (ETH) price: {eth_price}")

