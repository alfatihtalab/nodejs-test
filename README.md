# nodejs-test 1

### Task: Implement a Magic Link API in Node.js with Docker Containerization

#### Description:
You are required to create a **Magic Link API** using Node.js, containerized with **Docker**. The API should allow a user to request a magic link by entering their email. A unique URL should be generated and sent to the user's email, allowing them to authenticate once the link is clicked. The magic link should expire after 30 minutes.

You are expected to handle **security** measures, **token expiration**, and provide a proper implementation of **email templates**. The magic link should verify the user, store the user’s details in the database, and perform handshaking to complete the authentication.

The application should be **containerized using Docker**, making it easy to run and deploy the application in any environment. The final project should be **published** on a **free cloud platform** (e.g., Heroku or Render) for testing purposes.

#### Requirements:
- **Technologies**:
  - Node.js (Express framework or Any framework)
  - Firebase or any other NoSQL database
  - JWT for token generation
  - Nodemailer for sending emails
  - Docker for containerization
  - Free Cloud Platform for deployment (Heroku/Render)
  
- **Functionality**:
  1. **Request Magic Link**:
     - User enters an email address.
     - The API sends a magic link containing a unique URL to the user's email.
     - Store the token in a database with a **30-minute expiration** time.
     
  2. **Verify Magic Link**:
     - When the user clicks on the link, verify the token.
     - If valid and not expired, mark the user as authenticated.
     - Store the user details in the database.
  
  3. **Security**:
     - Ensure the token is **unique** and cannot be reused.
     - Implement necessary security headers, rate limiting, and proper validation.
     - Use HTTPS to secure the communication.

  4. **Docker**:
     - Containerize the Node.js app using **Docker**.
     - Create a `Dockerfile` to build the app's image.
     - Add a `docker-compose.yml` file to spin up the app with the necessary services (e.g., Node.js and MongoDB containers).

  5. **Deployment**:
     - Publish the containerized API to a free cloud service (e.g., **Heroku** or **Render**).
     - Provide the public URL for the API.

#### Steps:
1. **User Flow**:
   - User submits an email to the API.
   - The API sends an email with a magic link.
   - The user clicks on the magic link, and the token is validated.
   - Upon successful validation, the user is saved to the database.
  
2. **Implementation**:
   - **API Routes**:
     - `POST /request-magic-link`: For requesting the magic link.
     - `GET /verify-magic-link/:token`: For verifying the magic link and completing the authentication.
     - `GET /users/:id`: For verifying the user registered and stored in the DB.

   - **Email Template**: 
     - Create a simple email template that includes the magic link.
   - **Database**:
     - Store user details and track the token’s expiration.

3. **Containerization**:
   - **Dockerfile**: 
     - Create a Dockerfile for building the Node.js application image.
     - Example:
       ```Dockerfile
       FROM node:18-alpine
       WORKDIR /usr/src/app
       COPY package*.json ./
       RUN npm install
       COPY . .
       EXPOSE 3000
       CMD ["npm", "start"]
       ```
   - **docker-compose.yml**:
     - Create a `docker-compose.yml` file to orchestrate Node.js and MongoDB containers.
     - Example:
       ```yaml
       version: '3'
       services:
         web:
           build: .
           ports:
             - "3000:3000"
           environment:
             - MONGO_URL=mongodb://db:27017/magic-link
         db:
           image: mongo
           volumes:
             - mongo-data:/data/db
       volumes:
         mongo-data:
       ```

4. **Deployment**:
   - Publish the containerized API to a free cloud service (Heroku/Render).
   - Provide the public URL for the API.
  
5. **Deliverables**:
   - Final **code zipped** with instructions and necessary commands to run the application using Docker.
   - Ensure the code is easy to follow and documented.
   - Add a **README** file explaining how to run the application locally using Docker.
   - Provide the **deployed API URL** for testing.

6. **Command to Run**:
   - To run the application locally using Docker:
     ```bash
     docker-compose up --build
     ```

7. **Testing Instructions**:
   - Test the API by submitting an email.
   - Check the inbox for the magic link.
   - Click the link to verify and observe the behavior.

### Suggestions for Cloud Hosting:
- **Heroku**: Provides free-tier hosting for Node.js applications with Docker support.
  - [Heroku Docker Deployment Guide](https://devcenter.heroku.com/articles/container-registry-and-runtime)
  
- **Render**: Another free option for deploying containerized applications.
  - [Render Docker Deployment Guide](https://render.com/docs/deploy-docker)

Good luck!
