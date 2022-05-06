SRC = docker-compose.yml
NAME = Inception

all: $(NAME)

$(NAME):
	docker-compose -f ${SRC} up --build -d 

clean:
	docker-compose -f ${SRC} stop

fclean: clean
	docker-compose -f ${SRC} down


prune: fclean
	docker image prune -a -f
	docker volume rm $$(docker volume ls -q)

re: fclean all

.PHONY: all clean flcean re setup

