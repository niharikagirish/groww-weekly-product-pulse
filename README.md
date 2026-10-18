# Groww Weekly Product Pulse

An AI-powered n8n workflow that analyses public Groww app reviews, generates a weekly product pulse, verifies fee information against official sources, and prepares follow-up actions subject to human approval.

## How to Run

1. Import the [main workflow](workflows/GROWW%20Weekly%20Product%20Pulse.json) and [MCP server workflow](workflows/MCP%20server.json) into n8n.
2. Configure AI, Gmail, and Google Docs credentials, then publish the MCP server and configure its Production URL in the main workflow.
3. Submit the Groww reviews CSV and execute the main workflow.
4. Review the report and approve or reject the proposed actions through the approval email.
5. After approval, verify the Google Docs update and Gmail draft. The customer-facing draft is not sent automatically.

## Where MCP Approval Happens

Human approval occurs in the Gmail **Send message and wait for response** node. The **Approved?** IF node routes execution based on the response. Only the approved branch proceeds to the MCP Client actions.

## Fee Issue Identified

Multiple reviews report concerns about high or unclear charges, including an allegation of duplicate brokerage. These are customer-reported concerns, not verified charging errors.

Fee information is checked against:
- [Groww Pricing](https://groww.in/pricing)
- [Groww Help Centre: Fees and Charges](https://groww.in/help/payments-&-withdrawals/payments-charges/what-fees-does-groww-charge--58)

## Project Outputs

- [Weekly Product Pulse](outputs/weekly-product-pulse.md)
- [Email Draft](outputs/email-draft.md)
- [Notes/Doc Entry](outputs/notes-doc-entry.md)
- [Source List](sources.md)

## Limitations

Findings depend on the supplied review sample and date coverage. Customer allegations require independent verification, and official fee policies should be rechecked before customer-facing use.
