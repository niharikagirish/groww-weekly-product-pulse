# Groww Weekly Product Pulse

## 1. How to Run

1. Import `workflows/GROWW Weekly Product Pulse.json` into n8n.
2. Import `workflows/MCP server.json` as a separate workflow.
3. Configure the required credentials for the AI model, Gmail and Google Drive/Docs.
4. Publish the MCP server workflow and configure its Production URL in the main workflow's MCP Client node.
5. Provide the Groww reviews CSV and ensure the official-source retrieval nodes are configured.
6. Execute the main workflow and review the generated report.
7. Approve or reject the proposed actions through the approval email.
8. After approval, verify the Google Doc update and Gmail draft creation. The customer-facing email is saved as a draft and is not sent automatically.

## 2. Where MCP Approval Happens

Human approval happens in the Gmail **Send message and wait for response** node. The `Approved?` IF node checks the response.

- **Approved:** the workflow proceeds to the MCP Client and attempts the configured Google Docs update and Gmail draft creation.
- **Rejected:** the workflow follows the rejection branch, and the approved actions should not execute.

## 3. Fee Issue Identified from Reviews

Multiple Groww reviews express concerns about high or unclear charges, including an allegation of duplicate brokerage: *“ब्रोकरेज चार्ज 2 बार लेता है”* (“It charges brokerage twice”).

These reviews indicate a recurring perception of fee-transparency problems. They do not independently establish that a particular charge was applied incorrectly. The fee explanation is checked against the official Groww sources listed in [`sources.md`](sources.md).
