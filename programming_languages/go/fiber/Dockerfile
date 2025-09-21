FROM golang:alpine AS build-stage

WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY *.go ./

RUN CGO_ENABLED=0 GOOS=linux go build -o /web_app

FROM build-stage AS run-test-stage
RUN go test -v ./...

FROM alpine AS build-release-stage

WORKDIR /

COPY --from=build-stage /web_app /web_app

EXPOSE 8080

USER nobody

ENTRYPOINT ["/web_app"]
