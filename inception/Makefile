DIR = /home/${USER}

all: inception

inception:
	sudo mkdir -p ${DIR}/data/mariadb
	sudo mkdir -p ${DIR}/data/wordpress
	sudo docker-compose -f ./srcs/docker-compose.yml up --build -d

clean:
	sudo docker-compose -f ./srcs/docker-compose.yml down --rmi all -v --remove-orphans 2>/dev/null || true

fclean: clean
	sudo rm -rf ${DIR}/data/*
	sudo docker rmi -f $$(docker images -a -q) 2> /dev/null || true
	sudo docker volume prune -f

re: fclean all

.PHONY: all clean fclean re
