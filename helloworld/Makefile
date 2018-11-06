.PHONY: all
all: .helloworld

REV := $(shell git log --max-count=1 --pretty="format:%h" HEAD)

.helloworld: helloworld-linux-amd64 Dockerfile
	docker build -t sebidude/helloworld:master-$(REV) .
	touch $@

helloworld-linux-amd64: helloworld.go
	env GOOS=linux GOARCH=amd64 go build -ldflags="-X main.rev=$(REV)" -o $@ $*

.PHONY: clean
clean:
	rm -f .helloworld helloworld-linux-amd64

