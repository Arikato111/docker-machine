default: down up

full-setup: up install-1.5b

up:
	@docker compose up -d

down:
	@docker compose down

install-7b:
	@docker exec -it ollama-service ollama pull deepseek-r1:7b

install-1.5b:
	@docker exec -it ollama-service ollama pull deepseek-r1:1.5b
