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
client_id = 
