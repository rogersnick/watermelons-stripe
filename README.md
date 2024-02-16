# Watermelon Demo Sales Page

![colorful watermelons on a laptop](./public/img/watermelon-computer.png)

This code implements a simple Stripe checkout sales page for selling watermelon emojis.

## Running locally

1. Install dependencies

~~~
npm install
~~~

1. Set environment variables. Create a local file called `.env` that contains the following:

```
STRIPE_API_KEY=sk_test_...
YOUR_DOMAIN=http://localhost:4242
IMAGE_URL=https://url-to-image-for-checkout
```

2. Run the server

~~~
npm start
~~~

3. Open up [http://localhost:4242/checkout.html](http://localhost:4242/checkout.html)

## Details and Customization

This basic express web server hooks users up with three important files from the `/public` folder: 

- _index.html_: The actual form that users will see which initiates a post to the backend.
- _success.html_: Displayed to users upon a successful purchase
- _winback.html_ - Displayed to users if they return from the purchase screen without completing a purchase

`/server.js` - basic express server for backend functionality. It exposes the following routes:

- `/create-checkout-session` that answers the post request from the client facing form and forwards the user to a payment page
- `/webhooks/stripe/` that receives webhook requests from stripe to keep track of how many watermelons there are right now
- `persist.js` very lightweight data store for storing number of watermelons
- 