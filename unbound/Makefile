COMPOSE=	docker-compose
SERVICE=	unbound


build:
	$(COMPOSE) build

up:
	$(COMPOSE) create
	$(MAKE) config
	$(COMPOSE) start

down:
	$(COMPOSE) down
		
cli:
	$(COMPOSE) exec $(SERVICE) bash

test:
	$(MAKE) up
	sleep 10
	$(MAKE) dig
	$(MAKE) down

dig:
	$(COMPOSE) exec $(SERVICE) dig @127.0.0.1 . DNSKEY +dnssec
	
reconfig: config
	$(COMPOSE) exec $(SERVICE) unbound-control reload

config:
	$(COMPOSE) cp unbound.conf $(SERVICE):/etc/unbound/unbound.conf
