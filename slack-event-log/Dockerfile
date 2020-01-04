FROM golang:latest as base

EXPOSE 8080

WORKDIR /go/src/app

COPY . .

RUN go get -v

RUN go build -o /go/bin/app

FROM alpine as prod
COPY --from=base /go/bin/app /slack-event-log
CMD ["/slack-event-log"]
