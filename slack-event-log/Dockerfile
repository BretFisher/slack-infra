FROM golang:latest as base

EXPOSE 8080

WORKDIR /go/src/app

COPY . .

RUN go get -d -v ./...

RUN go build -o /go/bin/app

FROM gcr.io/distroless/base as prod
COPY --from=base /go/bin/app /slack-event-log
ENTRYPOINT ["/slack-event-log"]
