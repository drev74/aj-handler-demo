AJIMG ?= drev74/aj-handler:test
HOST  ?= '192.168.1.93:34377'
CTX 	?= AJC

show:

build:
	cd docker && ajc package docker --file build.yml

release:
	cd docker && docker build . -t ${AJIMG}

run:
	docker run -it \
		-v ${PWD}/nats:/handler/config/nats \
	 	-p 8087:8080 \
	 	--rm ${AJIMG}

.PHONY: build release run