# Build environment
# -----------------
FROM golang:1.13-alpine as build-env
WORKDIR /servicea
RUN apk update && apk add --no-cache gcc musl-dev git
COPY . .
RUN go build -ldflags '-w -s' -a -o ./bin/app ./cmd/app


# Deployment environment
# ----------------------
FROM alpine
RUN apk update
COPY --from=build-env /servicea/bin/app /servicea/
EXPOSE 8080
CMD ["/servicea/app"]