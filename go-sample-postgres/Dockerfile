FROM golang:1.22.3

# Set working directory to /myapp
WORKDIR /myapp

# Run "go version" to ensure Go is correctly installed
RUN go version

# Copy go.mod and go.sum to download dependencies
COPY go.mod go.sum ./
RUN go mod download

# Copy all Go source files into the image
COPY *.go ./

# Copy AUTHORS.md before building the Go application
COPY AUTHORS.md ./

# Build the Go application with the output name "my-go-app"
RUN CGO_ENABLED=0 GOOS=linux go build -o /myapp/my-go-app

# Copy LINKS.md after the build
COPY LINKS.md ./

# Expose the port that the app will listen on (e.g., 8080)
EXPOSE 80

# Command to run the application
CMD ["/myapp/my-go-app"]

# Example of how to build and run the Docker container
# docker build -t my-go-dockerfile .
# docker run -d -p 8085:8080 --name my-go-container my-go-dockerfile
