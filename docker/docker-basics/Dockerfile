# Use existing docker image as base
FROM alpine

# Download and install dependency
RUN apk add --update redis
RUN apk add --update gcc

# Run following command once container has started
CMD ["redis-server"]