=============================
Amazon Payment Services (APS)
=============================

`Amazon Payment Services <https://flutterwave.com/>`_ or APS is an online payment provider
established in Dubai offerint several online payment options.

.. _payment_acquirers/aps/configure_dashboard:

Configuration on APS Dashboard
==============================

#. Log into your `Amazon Payment Services Dashboard <https://testfort.payfort.com/>`_ and go to
   :menuselection:`Integration Settings --> Security Settings`. Generate the
   :guilabel:`Access Code` if none has been generated yet. Copy the values of the
   :guilabel:`Merchant Identifier`, :guilabel:`Access Code`, :guilabel:`SHA Request Phrase` and
   :guilabel:`SHA Response Phrase` fields and save them for later.
#. Enter your Odoo database URL in the :guilabel:`Origin URL`, for example:
   `https://yourcompany.odoo.com/`. Then click on :guilabel:`Save Changes`.
#. Navigate to :menuselection:`Integration Settings --> Technical Settings` and click on
   :guilabel:`Redirection`. Make sure :guilabel:`Status` is set to `Active` and select your
   preferred payment methods underneath in :guilabel:`Payment Options`.
#. | Set :guilabel:`Send Response Parameters` to :guilabel:`Yes` and enter your database URL
     followed by `/payment/aps/return` in the :guilabel:`Redirection URL`.
   | For example `https://yourcompany.odoo.com/payment/aps/return`.
   | Enter your database URL followed by `/payment/aps/webhook` in the
     :guilabel:`Direct Transaction Feedback` and :guilabel:`Notification URL` field.
   | For example `https://yourcompany.odoo.com/payment/aps/webhook`.
#. Under :menuselection:`Integration Settings --> Payment Page Template` you can customize the
   look and feel of the Amazon Payment Services payment page (where customers fill out their
   credit card details during operations).

.. _payment_acquirers/aps/configure_odoo:

Configuration on Odoo
=====================

#. :ref:`Navigate to the payment acquirer Amazon Payment Services <payment_acquirers/add_new>` and
   change its state to :guilabel:`Enabled` and make sure it is :guilabel:`Published`.
#. In the :guilabel:`Credentials` tab, fill the :guilabel:`Merchant Identifier`,
   :guilabel:`Access Code`, :guilabel:`SHA Request Phrase` and :guilabel:`SHA Response Phrase` with
   the values you saved at the step :ref:`payment_acquirers/aps/configure_dashboard`.
#. Configure the rest of the options to your liking.

.. _aps/local-payment-methods:

Enable local payment methods
============================

Local payment methods are payment methods that are only available for certain merchants and
customers countries and currencies.

Amazon Payment Services supports the following local payment methods:

- Mada
- Sadad

To enable specific local payment methods with Amazon Payment Services, list them as supported
payment icons. To do so, go to :menuselection:`Payment Acquirers --> Stripe --> Configuration` and
add the desired payment methods in the **Supported Payment Icons** field. If the desired payment
method is already listed, you don't have anything to do. If a payment icon record doesn't exist in
the database, its related payment method is considered enabled with Amazon Payment Services.

.. seealso::
   - :doc:`../payment_acquirers`

