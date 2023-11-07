FROM golang:1.21 as builder
WORKDIR /build
COPY . .
RUN go mod download
RUN CGO_ENABLED=0 go build -o /build/bin/app
FROM gcr.io/distroless/static-debian12:latest-amd64
COPY --from=builder /build/bin/app /
CMD ["/app"]
