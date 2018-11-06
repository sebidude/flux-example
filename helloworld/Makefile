.PHONY: all
all: .helloworld

VERSION := 1.0.1

.helloworld: helloworld-linux-amd64 Dockerfile
	docker build -t sebidude/helloworld:$(VERSION) .
	touch $@
	docker push sebidude/helloworld:$(VERSION)

helloworld-linux-amd64: helloworld.go
	env GOOS=linux GOARCH=amd64 CGO_ENABLED=0 go build -ldflags='-extldflags "-static" -d -s -w -X main.rev=$(VERSION)' -o $@ $*

.PHONY: clean
clean:
	rm -f .helloworld helloworld-linux-amd64

