TEST?=$$(go list ./... |grep -v 'vendor')

default: build

build: 
	go build

test:
	go test -i $(TEST) || exit 1
	echo $(TEST) | \
		xargs -t -n4 go test $(TESTARGS) -timeout=30s -parallel=4

testacc:
	TF_ACC=1 go test $(TEST) -v $(TESTARGS) -timeout 120m

testcov: 
	test -coverprofile=c.out && go tool cover -html=incapsula/c.out

install: 
	go install