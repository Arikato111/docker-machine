default:
	@echo no default
tag := latest
build:
	docker build -t arikato111/ryu:$(tag) .

rm:
	docker rmi arikato111/ryu:$(tag)
