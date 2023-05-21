############################
# STEP 1 build executable binary
############################
FROM golang:alpine AS base

WORKDIR $STUDY_PATH/task/go

RUN mkdir -p /go/src/fullcycle
COPY message.go /go/src/fullcycle

WORKDIR /go/src/fullcycle/
RUN go mod init message
RUN go mod tidy
RUN CGO_ENABLED=0 GOOS=linux go build -o message
#debug proporse
#RUN ls /go/src/fullcycle

############################
# STEP 2 build a small image
############################
FROM scratch

# Copy our static executable.
COPY --from=base /go/src/fullcycle/message /go/src/fullcycle/message
#RUN ls -lha /go/src/fullcycle/
CMD ["/go/src/fullcycle/message"]
