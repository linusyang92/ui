all: fetch test-ui-32.exe test-ui.exe

fetch:
	go get -d ./...

test-ui-32.exe: main.go
	MARCH=i686; CC=$$MARCH-w64-mingw32-gcc CXX=$$MARCH-w64-mingw32-g++ \
	GOOS=windows GOARCH=386 CGO_ENABLED=1 \
	go build -v -o $@ \
	-ldflags="-s -w -extld=$$MARCH-w64-mingw32-g++ -H=windowsgui" $<

test-ui.exe: main.go
	MARCH=x86_64; CC=$$MARCH-w64-mingw32-gcc CXX=$$MARCH-w64-mingw32-g++ \
	GOOS=windows GOARCH=amd64 CGO_ENABLED=1 \
	go build -v -o $@ \
	-ldflags="-s -w -extld=$$MARCH-w64-mingw32-g++ -H=windowsgui" $<

clean:
	rm -f *.exe

.PHONY: all fetch clean
