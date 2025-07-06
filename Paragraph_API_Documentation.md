Paragraph Word Search API - Design & Run Documentation
=======================================================

1\. Overview \-\-\-\-\-\-\-\-\-\-- A RESTful API to submit paragraphs,
tokenize and index words, and search for paragraphs containing a
specific word.

Tech stack: Django REST Framework, PostgreSQL, JWT Authentication,
Docker.

2\. System Design \-\-\-\-\-\-\-\-\-\-\-\-\-\-\-- - Users: Custom user
model with UUID, name, email, dob, createdAt, modifiedAt. - Paragraphs:
Stored with unique UUIDs, linked to users. - Word Indexing:  -
Paragraphs split by two newlines.  - Words are lowercased,
whitespace-tokenized.  - Indexed into a WordIndex model with (word,
paragraph) uniqueness. - Search: Returns top 10 paragraphs containing a
word. - Authentication: All write/search APIs require JWT access
token. - Docs: Swagger UI (/swagger/) and Postman collection included.

3\. Running the Project (Using Docker)
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
Prerequisites: Docker & Docker Compose

Step-by-step: 1. Clone the repo: git clone
https://github.com/your-username/paragraph-api.git cd paragraph-api

2\. Add environment variables: Create a file named \`.env\` with:
DB_NAME=paragraphdb DB_USER=postgres DB_PASSWORD=postgres DEBUG=True
SECRET_KEY=your_secret_key

3\. Build and start the containers: docker-compose build docker-compose
up

4\. Run migrations and create a superuser: docker-compose exec web
python manage.py migrate docker-compose exec web python manage.py
createsuperuser

Visit http://localhost:8000/

4\. Key Endpoints \-\-\-\-\-\-\-\-\-\-\-\-\-\-\-- \| Method \| URL \|
Description \|
\|\-\-\-\-\-\-\--\|\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\|\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\|
\| POST \| /api/register/ \| Register a new user \| \| POST \|
/api/login/ \| Login and receive JWT tokens \| \| POST \|
/api/paragraphs/ \| Submit multiple paragraphs \| \| GET \|
/api/search/?word=example \| Search top 10 paragraphs \| \| GET \|
/swagger/ \| Swagger UI \| \| GET \| /redoc/ \| Redoc documentation \|

5\. Postman \-\-\-\-\-\-\-\-\-- - Import the provided
Paragraph_API.postman_collection.json into Postman - Run Register →
Login → Submit Paragraphs → Search

6\. Folder Structure \-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
paragraph-api/ ├── core/ ├── backend/ ├── requirements.txt ├──
Dockerfile ├── docker-compose.yml ├── .env ├── README.md

7\. Submission \-\-\-\-\-\-\-\-\-\-\-\-- - Push code to GitHub
(private) - Include Postman collection - Share repo access with
ravi.bhalani@codemonk.io

Author: Your Name Email: yourname@example.com
