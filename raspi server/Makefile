raspi-update:
	@sudo apt update
	@sudo apt upgrade -y
raspi-disk:
	@df -h

install-docker:
	curl -sSL https://get.docker.com | sh
	echo "Check doker version after install"
	docker --version
	echo "Run first doker after install"
	docker run hello-world

install-omv:
	wget -O - https://github.com/OpenMediaVault-Plugin-Developers/installScript/raw/master/install | sudo bash
	echo "Install OMV succesfull user name: admin password: openmediavault"

docker-install-portainer:
	/dockerfile/portainer/docker-compose up -d

docker-install-plex:
	/dockerfile/plex/docker-compose up -d