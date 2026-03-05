
FROM golang:1.25.6-alpine AS build

WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY . .

RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o checkoutservice .


FROM alpine:3.19

WORKDIR /app

COPY --from=build /app/checkoutservice .

EXPOSE 5050

CMD ["./checkoutservice"]
