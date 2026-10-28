# SmartCommerce AI

### AI-Powered E-Commerce Order & Customer Inquiry Automation Using n8n

SmartCommerce AI is an AI-powered email automation system built using **n8n, OpenAI, Gmail, and Google Sheets**. It helps online stores manage customer order requests and product inquiries by classifying incoming emails, extracting information, recording orders, and preparing personalized email responses.

The system uses AI-powered classification to route customer emails into two separate workflows.

## Workflow Overview

![SmartCommerce AI n8n Workflow](smartcommerce-workflow.png)

## Key Features

- **Intelligent Email Classification:** Automatically identifies customer orders and product inquiries.
- **Order Information Extraction:** Extracts customer names, products, quantities, and special instructions.
- **Order Validation:** Checks whether essential order details are present before processing.
- **Google Sheets Integration:** Stores valid customer orders in a structured database.
- **Missing Information Handling:** Generates email drafts requesting missing order details.
- **Product Inquiry Automation:** Retrieves product information from Google Sheets and answers customer questions.
- **Stock Availability Responses:** Handles available, out-of-stock, and unknown products.
- **Human-in-the-Loop Communication:** Creates Gmail drafts for review rather than automatically sending responses.

## Workflow Architecture

**1. Email Classification**

`Gmail Trigger → AI Text Classifier`

The classifier identifies whether an incoming email is an Order or Inquiry.

**2. Order Automation Branch**

`Information Extractor → IF Validation → Google Sheets → OpenAI → Gmail Draft`

For incomplete orders:

`IF (Missing Details) → OpenAI → Gmail Draft`

**3. Product Inquiry Branch**

`Google Sheets Product Lookup → Aggregate → OpenAI → Gmail Draft`

The Aggregate node combines product records into one item, allowing the AI to analyze the product database and generate a single response.

## Technologies Used

| Technology | Purpose |
|---|---|
| n8n | Workflow orchestration |
| OpenAI GPT-4o-mini | Classification, extraction, and email generation |
| Gmail | Email triggers and draft creation |
| Google Sheets | Orders and product database |
| Aggregate Node | Combine product data |
| IF Node | Validate required order information |

## Testing & Results

The workflow was tested with the following scenarios:

- Valid order containing customer information, product, quantity, and delivery instructions.
- Incomplete order with missing quantity.
- Product inquiry for an available product.
- Product inquiry for an out-of-stock product.
- Inquiry for a product not listed in the database.
- Correct email classification and Gmail draft generation.

These scenarios produced the expected results during testing.

## How to Set Up

1. Download the workflow JSON from this repository.
2. Import the JSON file into your n8n instance.
3. Configure your OpenAI and Gmail credentials.
4. Create a Google Sheets database containing `Orders` and `Products` tabs.
5. Connect the Google Sheets nodes to your own spreadsheet.
6. Configure the required sheet columns and field mappings.
7. Activate the workflow and test it using sample customer emails.

**Note:** Credentials and private spreadsheet identifiers are not included in the shared workflow. You must configure your own connections.

## Future Improvements

- Inventory validation before accepting orders.
- Automatic order status tracking.
- Customer notifications.
- Integration with an e-commerce platform.
- Advanced customer support using RAG.

## Project Status

**Completed prototype — core Order and Inquiry workflows tested successfully.**

Built as a hands-on AI automation project using n8n.

## Feedback

Suggestions and feedback are welcome! Feel free to open an issue or share ideas for improving this workflow.

---

**If you find this project useful, consider giving the repository a star!**
