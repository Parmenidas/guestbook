# Use golang image
FROM golang:1.18 as builder

# Working directory
WORKDIR /app

# Copy files 
COPY main.go .

# Buil app
RUN go mod init guestbook
RUN go mod tidy

RUN go build -o main main.go

FROM ubuntu:18.04

COPY --from=builder /app/main /app/guestbook

ADD public/index.html /app/public/index.html
ADD public/script.js /app/public/script.js
ADD public/style.css /app/public/style.css
ADD public/jquery.min.js /app/public/jquery.min.js

WORKDIR /app

# Default command
CMD ["./guestbook"]

# Port 3000
EXPOSE 3000
