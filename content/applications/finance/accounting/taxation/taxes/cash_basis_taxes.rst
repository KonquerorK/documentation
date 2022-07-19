================
Cash basis taxes
================

Cash basis taxes are due when the payment is made, as opposed to standard taxes that are due when
the invoice is confirmed. Reporting your income and expenses to the administration based on the cash
basis method is mandatory in some countries and under some conditions.

.. example::
   You sell a product in the 1st quarter of your fiscal year and the payment is received in the 2nd
   quarter. Based on the cash basis method, the tax you must pay to the administration is due for
   the 2nd quarter.

Configuration
-------------

To configure taxes using cash basis, go to :menuselection:`Accounting --> Configuration -->
Settings --> Taxes` and enable :guilabel:`Cash Basis`.

Then, define the :guilabel:`Tax Cash Basis Journal`. Click on the external link available next to
the journal to update information such as :guilabel:`Journal Name`, :guilabel:`Type` or
:guilabel:`Short Code` that displays the journal entries of this journal.

.. image:: cash_basis_taxes/tax_cash_basis_journal.png
    :align: center
    :alt: Select your Tax Cash Basis Journal and click on the external link

.. note::
   By default, the journal entries of the :guilabel:`Cash Basis Taxes` journal are named using the
   :guilabel:`CABA` short code.

Once this is done, go to :menuselection:`Accounting --> Configuration --> Accounting: Taxes` to
configure your taxes. You can either :guilabel:`Create` a new tax or update an existing one,
clicking on it.

The :guilabel:`Account` column reflects the proper transitional accounts to post taxes until the
payment is registered.

.. image:: cash_basis_taxes/account_column.png
    :align: center
    :alt: Fill in the account column with a transitional accounts where taxes go until the payment
       is registered

In the :guilabel:`Advanced Options` tab, decide of the :guilabel:`Tax Exigilibity`. Select
:guilabel:`Based on Payment`, so the tax is due as soon as the payment of the invoice is received.
You can then also define the :guilabel:`Cash Basis Transition Account` where the tax amount is as
long as the original invoice has not been reconciled.

.. image:: cash_basis_taxes/advanced_options.png
    :align: center
    :alt: Fill in the Cash Basis Transition Account where taxes amounts go until payment
        reconciliation.

Impact of cash basis taxes on accounting
----------------------------------------

To illustrate the impact of cash basis taxes on the accounting, let’s take an example with the sales
of a product that costs 1.000$, with a 15% cash basis tax.

.. image:: cash_basis_taxes/customer_invoice_with_cbt.png
    :align: center
    :alt:

The following entries are created in your accounting and the tax report is currently empty.

+----------------------------+----------------------------+
|**Customer journal (INV)**                               |
+============================+============================+
| **Debit**                  |**Credit**                  |
+----------------------------+----------------------------+
| Receivable $1.150          |                            |
+----------------------------+----------------------------+
|                            |Income $1.000               |
+----------------------------+----------------------------+
|                            |Temporary tax account $150  |
+----------------------------+----------------------------+

When the payment is then received, it is registered as below :

+----------------------------+----------------------------+
| **Bank journal (BANK)**                                 |
+============================+============================+
| **Debit**                  |**Credit**                  |
+----------------------------+----------------------------+
| Bank $1.150                |                            |
+----------------------------+----------------------------+
|                            |Receivable $1.150           |
+----------------------------+----------------------------+

.. note::
    Once the payment registered, a smart button :guilabel:`Cash Basis Entries` appears on the
    invoice and redirects you to the :guilabel:`Cash Basis entries`.

Finally, upon reconciliation of the invoice with the payment, the below entry is automatically
created by Odoo:

+----------------------------+----------------------------+
| **Tax Cash Basis Journal (Caba)**                       |
+============================+============================+
| **Debit**                  |**Credit**                  |
+----------------------------+----------------------------+
| Income account $1.000      |                            |
+----------------------------+----------------------------+
| Temporary tax account $150 |                            |
+----------------------------+----------------------------+
|                            |  Income account $1.000     |
+----------------------------+----------------------------+
|                            | Tax Received $150          |
+----------------------------+----------------------------+

The journal items Income account vs. Income account are neutral but they are needed to ensure
correct tax reports in Odoo with accurate base tax amounts.

Using a default :guilabel:`Base Tax Received Account` is recommended so your balance is at zero and
your income account is not polluted by unnecessary accounting movements. To configure a default
:guilabel:`Base Tax Received Account`, go to :menuselection:`Accounting --> configuration -->
Settings`.
