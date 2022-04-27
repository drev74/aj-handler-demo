AJIMG ?= drev74/aj-handler:test
CTX 	?= AJ_API

show:

build:
	cd docker && ajc package docker --file build.yml

release:
	cd docker && docker build . -t ${AJIMG}

context:
	XDG_CONFIG_HOME=`pwd` nats context add ${CTX} --server nats://localhost:4222 && chmod 777 -R nats 

run:
	docker run -it -v ${PWD}/nats:/handler/config/nats -e AJ_NATS_CONTEXT=${CTX} -p 8087:8080 --rm ${AJIMG}

.PHONY: build release context run