# **AI-PDF**

<img src="./assets/AIPDFHomepage.png" height="450" width="900" />

## **Table of Contents**

-   [License](#license)
-   [Project Overview](#project-overview)
-   [Purpose and Inspiration](#purpose-and-inspiration)
-   [Issues](#issues)
-   [Technologies Used](#technologies-used)

## **License**

This project is licensed under the MIT license.

## **Project Overview**

AI-PDF is an AI document scanner. The user loads a PDF to Amazon S3, and can then ask the AI any question they like regarding the uploaded files. If needed, the AI can pinpoint the page where it found the information.

Due to the confidentiality of the materials, I added a login authentication using Clerk.

<img src="./assets/AIPDFClerk.png" height="450" width="900"/>

## **Purpose and Inspiration**

My client had many PDF’s that they had to visually parse when looking for specific information, such as company protocols and specific regulations. They reached out and asked if I could make this task easier.

## **Issues**

Large Size PDF’s
Due to the large sizes of the PDF’s, the large file sizes prevented uploading through the standard 'file upload' feature on the homepage. To get around this, I set up an Amazon S3 account that is shared with my client. This way they can upload the content from the database, avoiding the 15-timeout issue.

## **Technologies Used**

Front End:

-   React.js
-   Next.js
-   TypeScript
-   TailwindCSS
-   Clerk Auth
-   Langchain
-   Openai-edge
-   Stripe
-   Open Library API

Back End:

-   Amazon S3
-   NeonDB
-   PineconeDB
-   PostgreSQL
-   Drizzle ORM

Due to this project containing sensitive information about their organization, the client requests that I do not share any data. If you wish to know more, please reach out and I can walk you through this project in greater detail.
