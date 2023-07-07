---
title: "Containerizing a go API with docker"
datePublished: Fri Jul 07 2023 07:18:56 GMT+0000 (Coordinated Universal Time)
cuid: cljs8wx34000009kw9koie0p9
slug: containerizing-your-app
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688713908368/a2d0e6aa-c306-4654-b660-39912785b5d5.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1688714318075/446eaf62-c2bd-4689-acc1-cad589548cc8.png
tags: docker, devops, containers, wemakedevs, getfitwithsagar

---

In my last blog, we explored the wonders of Docker. Now, it's time to put Docker to use as our container. If you missed the previous blog, I recommend giving it a read first. [Click here](https://souravk.hashnode.dev/containers-and-docker-simplifying-application-deployment). In this blog, we'll dive into the practical side of Docker and discover how it simplifies software packaging and deployment. Get ready to witness the magic of Docker as our powerful container. Let's begin this exciting journey together!

# GO API

<iframe src="https://giphy.com/embed/DeqfmaWh6CQOxmbhDS" width="480" height="480" class="giphy-embed"></iframe>

[via GIPHY](https://giphy.com/gifs/brzinsurance-brz-golang-brzwithgolang-DeqfmaWh6CQOxmbhDS)

I have been learning Golang so I'm using Golang as my Programming language you can choose any preferred language. So this API is just a simple API that handles one GET route and returns some JSON data.

```go
package main

import (
	"fmt"
	"net/http"

	"github.com/gin-gonic/gin"
)

// album represents data about a record album.
type album struct {
	ID     string  `json:"id"`
	Title  string  `json:"title"`
	Artist string  `json:"artist"`
	Price  float64 `json:"price"`
}

// albums slice to seed record album data.
var albums = []album{
	{ID: "1", Title: "Blue Train", Artist: "John Coltrane", Price: 56.99},
	{ID: "2", Title: "Jeru", Artist: "Gerry Mulligan", Price: 17.99},
	{ID: "3", Title: "Sarah Vaughan and Clifford Brown", Artist: "Sarah Vaughan", Price: 39.99},
}

// getAlbums responds with the list of all albums as JSON.
func getAlbums(c *gin.Context) {
	c.IndentedJSON(http.StatusOK, albums)
}

func main() {
	router := gin.Default()
	router.GET("/get", getAlbums)
	fmt.Println("Server is started")
	router.Run("localhost:8080")
}
```

We are building a basic API using Go. The API has one GET route that returns JSON data. Here's a breakdown of the steps:

1. We define a struct called `album` to represent an album.
    
2. Some example album data is created and stored in a album slice
    
3. The `getAlbums()` function retrieves the album data and converts it to JSON format.
    
4. In the `main()` function:
    
    * We create a router to handle our API routes.
        
    * We define a handler function for the "/get" route.
        
    * The handler sets the response content type to JSON and sends the album data as the response.
        
5. Finally, the server starts listening on port 8080.
    

When the program is executed and you visit [`http://localhost:8080/get`](http://localhost:8080/get) in a browser, you will receive JSON data containing information about the albums.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688627722078/a7fed1b2-1aef-4e2c-b6dd-c2df3b758e89.png align="center")

This is how it looks in the terminal when you run the program.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688627781126/5dd4a5ec-fd26-45e6-9d24-d57930ed5762.png align="center")

This is the output you will get when you run the program.

# Dockerfile

Now that our API is up and running on your local machine, it's time to make it easily shareable with others by containerizing it. This ensures that when you send your hard work to someone else, they won't run into compatibility issues or say, "It's not working on my computer."

To containerize our application, we need to create a Dockerfile. This file contains instructions for building a Docker image. Don't worry if you're not familiar with Dockerfile syntax; we can easily find the necessary information online.

Start by searching for "Dockerfile for Golang" to find relevant examples and documentation. You'll likely end up on the official Docker documentation page, which provides detailed explanations for various programming languages, including Go. Follow the step-by-step instructions outlined there.

By following the recommended steps, you'll be able to write a Dockerfile specific to your Go application. This Dockerfile will enable others to build a Docker image of your application and run it on their machines without any issues.

```dockerfile
#this will be our base image to run our go program
FROM golang:1.20

#now i'm creating the working dir so that everything can happen in on dir. just after creating the folder it move to that folder
WORKDIR /app

#now i have coped the go.mod and go.sum file into the working dir which is app
COPY go.mod go.sum ./

#now I run the commnad to download all the packages the is requred to run the go api
RUN go mod download && go mod verify

#next thing we need to do is to copy our source code into the image. We’ll use the COPY command just like we did with our module files before.
COPY *.go ./

# Note here: CGO_ENABLED is disabled for cross system compilation
# It is also a common best practise.

# Build the application.
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o /go-api

#now it time to run the program
CMD [ "/go-api" ]
```

Now that our Dockerfile is ready, we can proceed to build and run the Docker image.

To build the Docker image, we will use the following command:

```dockerfile
docker build -t go-api:v1 .
```

This command tells Docker to build an image based on the instructions in the Dockerfile. The `-t` flag specifies the image name (`go-api:v1` in this case), and the `.` indicates that the Dockerfile is located in the current directory.

Once the image is built, you can verify its existence by running the command:

```dockerfile
docker images
```

This command lists all the Docker images on your machine, and you should see `go-api:v1` among them.

To run the Docker image, use the following command:

```dockerfile
docker run go-api:v1
```

This command instructs Docker to create a container from the `go-api:v1` image and start running it. You should now be able to access your API by visiting the appropriate URL or endpoint.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688629276269/1a91f1bf-1aa4-46a5-b8a7-748f4c5a7cd6.png align="center")

As you can see it's running I'm going to use the curl command to get the JSON data.

`curl HTTP://localhost:8080/get`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688630252044/9dfbe923-9e4d-42d2-bf14-7349dfd2da7b.png align="center")

<iframe src="https://giphy.com/embed/BfNehJ7C7iC7XkjCkE" width="480" height="270" class="giphy-embed"></iframe>

[via GIPHY](https://giphy.com/gifs/hunchback-nice-noice-hunchback-music-BfNehJ7C7iC7XkjCkE)

# What do we learn?

In summary, we learned how to containerize our application using Docker. We created a Dockerfile to define the setup and dependencies, built a Docker image using `docker build`, and ran the image with `docker run`. This allows us to easily share and run our application on different machines without compatibility issues. Docker simplifies packaging and deployment, making our lives as developers much easier.