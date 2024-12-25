raspi-update:
	@sudo apt update
	@sudo apt upgrade -y
raspi-disk:
	@df -h

copy-thisfile:
	@echo "Copy ca thu mu nay toi raspi4 voi username va thu muc cung nhau"
	scp -v -r . root@phuclan-omv.local:~
	# scp -v Makefile root@raspi4:~

run-docker-compose:
	docker compose up -d

remove-docker-compose:
	# docker compose down --volumes 
	docker compose down

install-docker:
	curl -sSL https://get.docker.com | sh
	@echo "Check doker version after install"
	@docker --version
	@echo "Run first doker after install"
	@sudo docker run hello-world

install-omv:
	wget -O - https://github.com/OpenMediaVault-Plugin-Developers/installScript/raw/master/install | sudo bash
	echo "Install OMV succesfull user name: admin password: openmediavault"

docker-install-portainer:
	sudo docker compose -f dockerfiles/portainer/docker-compose.yml up -d

docker-install-plex:
	sudo docker compose -f dockerfiles/plex/docker-compose.yml up -d

docker-install-homer:
	sudo docker compose -f dockerfiles/homer/docker-compose.yml up -d

docker-install-pi-hole:
	sudo docker compose -f dockerfiles/pi-hole/docker-compose.yml up -d

docker-install-next-alert:
	@echo "Tao thu muc config voi permission wriable cho container"
	# mkdir ./dockerfiles/next-alert/netalertx/
	# mkdir ./dockerfiles/next-alert/netalertx/db/
	# mkdir ./dockerfiles/next-alert/netalertx/config/
	@echo "ko co permission cho db and config nen tam dung container data"

	sudo docker compose -f dockerfiles/next-alert/docker-compose.yml up -d

docker-install-next-cloud:
	sudo docker compose -f dockerfiles/next-cloud/docker-compose.yml up -d

install-plex-media:
	sudo apt update && sudo apt upgrade
	sudo apt install apt-transport-https -y
	curl https://downloads.plex.tv/plex-keys/PlexSign.key | gpg --dearmor | sudo tee /usr/share/keyrings/plex-archive-keyring.gpg >/dev/null
	echo deb [signed-by=/usr/share/keyrings/plex-archive-keyring.gpg] https://downloads.plex.tv/repo/deb public main | sudo tee /etc/apt/sources.list.d/plexmediaserver.list
	sudo apt update && sudo apt install plexmediaserver -y
	sudo systemctl enable --now plexmediaserver
	sudo systemctl status plexmediaserver