FROM golang:alpine AS builder
WORKDIR /workspace

COPY reverse-tunnel/ ./
RUN go mod download

ARG GOARCH
ARG GOARM
RUN GOARCH=${GOARCH} GOARM=${GOARM} CGO_ENABLED=0 go build

FROM gcr.io/distroless/static
COPY --from=builder /workspace/reverse-tunnel /bin
ENTRYPOINT ["reverse-tunnel"]
