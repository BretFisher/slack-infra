FROM golang:1.11 as base

EXPOSE 8080

ENV CGO_ENABLED=0

WORKDIR /go/src/app

COPY . .

RUN go get -v

RUN go build -o /go/bin/app

FROM debian:10-slim as prod
COPY --from=base /go/bin/app /slack-event-log
CMD ["/slack-event-log"]
