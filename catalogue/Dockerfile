# FROM node:20
# RUN addgroup -S roboshop && adduser -S roboshop -G roboshop # aphine syntax to add user 
# WORKDIR /opt/server
# RUN chown -R roboshop:roboshop /opt/server
# USER roboshop
# COPY package.json .
# COPY *.js .
# RUN npm install

# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node","server.js"]

#Multi stage #multi stage copy syntax

FROM node:20-alpine3.21 AS builder
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN npm install

FROM node:20-alpine3.21
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop # aphine syntax to add user 
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
WORKDIR /opt/server
USER roboshop
COPY --from=builder /opt/server /opt/server 
CMD ["node","server.js"]



#Ah! Now I see the problem. Even though your Dockerfile is using Alpine and switching to roboshop, package.json and server.js are still owned by root. That happens because in your Dockerfile you copied the files after switching to roboshop, but the Alpine COPY instruction runs as root by default, not the current user. The USER roboshop only affects runtime, not build-time COPY.



# # Base image
# FROM node:20-alpine3.21

# # Create roboshop user and group
# RUN addgroup -S roboshop && adduser -S roboshop -G roboshop

# # Create app directory and assign ownership
# RUN mkdir -p /opt/server && chown -R roboshop:roboshop /opt/server
# WORKDIR /opt/server

# # Switch to roboshop user
# USER roboshop

# # Copy application files
# COPY package.json .
# COPY *.js .

# # Install dependencies
# RUN npm install

# # Set environment variables
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"

# # Start application
# CMD ["node", "server.js"]
