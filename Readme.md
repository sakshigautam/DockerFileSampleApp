Step-by-Step Dockerfile Explanation

Line 1: FROM node:18
“We start by telling Docker which base image to use. node:18 is an official image from Docker Hub that has Node.js version 18 pre-installed.”

Line 2: WORKDIR /usr/src/app
“This sets the working directory in our container. Any command that follows will run from this directory.”

Line 3: COPY package*.json ./
“This copies both package.json and package-lock.json into the container. The asterisk * is a wildcard.”

Line 4: RUN npm install
“Here, we install the dependencies defined in the package files. This step is cached by Docker, which helps speed up rebuilds.”

Line 5: COPY . .
“Now, we copy the rest of the project files into the container. This includes app.js and any other files.”

Line 6: EXPOSE 3000
“We expose port 3000 so Docker knows this container will use that port. It's informational unless you use Docker’s networking features.”

Line 7: CMD ["node", "app.js"]
“This is the command that runs when the container starts. We’re telling it to run node app.js.”

How to Build and Run

# Build the image
docker build -t docker-sample-app .

# Run the container
docker run -p 3000:3000 docker-sample-app
