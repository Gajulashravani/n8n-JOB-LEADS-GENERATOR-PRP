# n8n-JOB-LEADS-GENERATOR-PRP
This n8n workflow scrapes job leads using user-provided inputs like job title and location. It automatically saves the results to a Google Sheet and sends a summary of the new listings to the user's email. You need to configure your own credentials for the Adzuna API, Google Sheets, and Gmail.

Job Leads Generator Workflow

This n8n workflow automates the process of generating and delivering job leads based on a user's specific criteria. It is a highly efficient tool for job seekers who wish to receive a curated list of job listings directly to their inbox without the need for manual, time-consuming searches.

#How the Workflow Functions

   Form Trigger: The entire process is initiated when a user interacts with and submits a public web form. This form is designed to collect all the necessary information to tailor the job search, including the desired Job Title, Location (chosen from a predefined list of Indian states), Job Type (Full-Time, Part-time), and the user's Email ID where the final results will be sent. The form's flexibility, including a multi-select option for job types, allows for highly specific search queries.

   Job Search via API: Once the form is submitted, the workflow makes an HTTP Request to a job search API, such as Adzuna. It dynamically constructs the API query using the user-provided inputs for job title and location. This ensures that the search is always relevant and up-to-date, fetching the latest job listings that match the user's requirements.

  Data Processing & Storage: The raw data received from the API is then processed and parsed. A Code node within the workflow extracts key details from each job listing, including the job's title, company name, location, description, pay range, and a direct link to the application page. This structured data is then sent to a Google Sheets node, where it is appended as a new row in a designated spreadsheet. This creates a centralized and easily accessible database of all scraped job leads.

   Email Notification: As the final step, the workflow uses another Code node to dynamically generate an HTML-formatted email. This email serves as a concise summary of the newly found jobs, presenting a clean list with essential details and a clickable link to apply for each position. The email also includes a link to the full Google Sheet, giving the user the option to view all the data. This email is then sent to the user's provided email address using a Gmail node, ensuring they receive the information in a clear and professional manner. The workflow is also designed to handle cases where no jobs are found, sending a polite email informing the user to check back later.


#Getting Started

To use this workflow, you need to import the provided job-leads-generator-PRP(2).json file into your own n8n instance.

Important: Before activating the workflow, you must configure the following credentials and details:

 1.Job API Credentials: You will need to obtain your own app_id and app_key from a job search API (like Adzuna) and add them to the HTTP Request node.

 2.Google Sheets Credentials: Set up a Google Sheets credential in your n8n instance and link it to the Append or update row in sheet node. You will also need to create your own Google Sheet and   update the documentId in the workflow's nodes.

 3.Gmail Credentials: The Send a message node requires a Gmail account credential to send emails.

 4.Update URLs: Ensure the spreadsheet URL in the Code1 node is updated to your own Google Sheet's URL so that users can access the full data.
