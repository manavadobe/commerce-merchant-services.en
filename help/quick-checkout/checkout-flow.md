---
title: "Checkout flow"
description: "Overview of the [!DNL Quick Checkout] flow in Adobe Commerce."
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
---
# [!DNL Quick Checkout] flow

This section provides an overview of the typical checkout experience using the [!DNL Quick Checkout] for Adobe Commerce extension.

A successful [!DNL Quick Checkout] flow consists of the following steps:

1. Open your storefront and add items in your cart.
1. Proceed to checkout.

  ![Checkout](assets/proceed-checkout.png)

1. When prompted, enter an email address associated with a [!DNL Bolt] account.
1. Input the One-Time Password (OTP) sent to that [!DNL Bolt] account’s email address or phone number.
1. Once logged in with your [!DNL Bolt] account, checkout details are automatically filled in:

   - Shipping information
   - Payment method
   
   >[!NOTE]
   >
   > You can use your existing wallet information (address or credit card information) even if your checkout details are automatically filled in.

1. Place Order.

The [!DNL Quick Checkout] is compatible with standard additional Adobe Commerce checkout options, such as [gift cards](https://docs.magento.com/user-guide/catalog/product-gift-card.html) or [discount codes](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Quick Checkout] use cases

The [!DNL Quick Checkout] allows for multiple use cases during a checkout flow:

- Guest user with a registered [!DNL Bolt] account.
- Guest user with a new [!DNL Bolt] account.
- An existing Adobe Commerce user with/without a registered [!DNL Bolt] account.

## Guest user checkout: How it works

Guest checkout experience is different from the logged-in experience. When a shopper enters an email address into checkout, the [!DNL Quick Checkout] validates it to find an existing [!DNL Bolt] account.

### Registered [!DNL Bolt] account

If a [!DNL Bolt] account is found, shoppers continue with their [!DNL Quick Checkout] seamless checkout experience: 

1. Input the One-Time Password (OTP) sent to that [!DNL Bolt] account’s email address or mobile, depending on user's preferences in the [!DNL Bolt] account.
1. Once logged in with your [!DNL Bolt] account, it fills the checkout details automatically:

   - Shipping information
   - Payment method

1. Place Order.

>[!TIP]
>
> Guest user places the order and can register in Adobe Commerce.

### New [!DNL Bolt] account

If no [!DNL Bolt] account is found, shoppers continue with their default out-of-the-box Adobe Commerce checkout and shopper provides all necessary details to place order:

- Shipping and billing information
- Shipping method
- Review payment method
- A checkbox appears to register in [!DNL Bolt] for faster checkouts before placing the order. They can agree to the terms & conditions to create their [!DNL Bolt] account.

   ![Remember [!DNL Bolt]](assets/checked-bolt.png)

- The guest user places the order and can register in Adobe Commerce.

## An existing Adobe Commerce user: How it works

An existing user can select existing details when user places an order with the [!DNL Quick Checkout] for a faster checkout experience.

When a shopper enters an email address into checkout, the [!DNL Quick Checkout] validates it to find an existing [!DNL Bolt] account.

### Registered [!DNL Bolt] account with an Adobe Commerce user

If a [!DNL Bolt] account is found, shoppers continue with their default out-of-the-box Adobe Commerce checkout and shopper provides all necessary details and then places order:

- Shipping and billing information
- Shipping method
- Review payment method

If you encounter issues when you place an order as an existing Adobe Commerce user, see the [Troubleshoot Quick Checkout issues](https://support.magento.com/hc/en-us/articles/6909450342541) article in the Adobe Commerce Help Center.

>[!NOTE]
>
> If user has a [!DNL Bolt] account and email does not appear as registered in Adobe Commerce, it triggers the One-Time Password (OTP) login. See the [registered [!DNL Bolt] account](#registered-bolt-account) flow.

### New [!DNL Bolt] account

If no [!DNL Bolt] account is found, shoppers continue with their default Adobe Commerce checkout and shopper selects all necessary details from their saved information to place the order:

- Shipping and billing information
- Shipping method
- Review payment method
- A checkbox appears to register in [!DNL Bolt] for faster checkouts before placing the order. They can agree to the terms & conditions to create their [!DNL Bolt] account.

  ![Remember [!DNL Bolt]](assets/checked-bolt.png)

## Get help

Contact [Adobe Commerce Support](mailto:quick-checkout-support@adobe.com) for any assistance.
