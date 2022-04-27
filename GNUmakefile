AJIMG ?= drev74/aj-handler:test
CTX 	?= AJC

show:

build:
	cd docker && ajc package docker --file build.yml

release:
	cd docker && docker build . -t ${AJIMG}

context:
	XDG_CONFIG_HOME=`pwd` nats context add ${CTX} --server nats://localhost:4222 && chmod 777 -R nats 

run:
	docker run -it \
	-v /home/bku/.config/nats:/handler/config/nats \
	 -e AJ_NATS_CONTEXT=${CTX} \
	 -e AJ_WORK_QUEUE=SDK \
	 -e XDG_CONFIG_HOME=/handler/config \
	 -p 8087:8080 \
	 --rm ${AJIMG}

.PHONY: build release context run