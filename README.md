# **AI-PDF**
<img src="Image of loaded stuff/>

## **Table of Contents**
- [License](#license)
- [Project Overview](#project-overview)
- [Purpose and Inspiration](#purpose-and-inspiration)
- [Issues](#issues)
- [Technologies Used](#technologies-used)

## **License**
This project is licensed under the MIT license.

## **Project Overview**
AI-PDF is an AI document scanner. The user loads a PDF either on the site or to AWS S3, and can ask the AI any question they like regarding the uploaded files. If needed, the AI can pinpoint the page where it found the information.

Due to the confidentiality of the materials, I added a login authentication using Clerk.

<img src="Image of Clerk authentication/>


## **Purpose and Inspiration**
My client had many PDF’s that she had to parse when looking for specific information, such as company protocols and specific regulations. They reached out and asked if I could make this task easier.

## **Issues**
Large Size PDF’s
Due to the large sizes of the PDF’s, the large file sizes prevented uploading through the standard 'file upload' feature on the homepage. To get around this, I set up an AWS S3 account that is shared with my client. This way they can upload the content from the database, avoiding the 15-timeout issue.

## **Technologies Used**

Front End:
* React.js
* Next.js
* TypeScript
* TailwindCSS
* Clerk Auth
* Langchain
* Openai-edge
* Stripe
* Open Library API

Back End:
* Amazon S3
* NeonDB
* PineconeDB
* PostgreSQL
* Drizzle ORM

Due to this project containing sensitive information about their organization, the client requests that I do not share any data. If you wish to know more, please reach out and I can walk you through this project in greater detail. 
