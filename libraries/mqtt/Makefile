ifeq ($(OS), Windows_NT)
remove_fun = del /S /Q $(subst /,\,$1)
else
remove_fun = rm -rf $(1)
endif

SRCS = mqtt_client.c mqtt_noos_support.c
SRCS += paho.mqtt.embedded-c/MQTTPacket/src/MQTTConnectClient.c\
	paho.mqtt.embedded-c/MQTTPacket/src/MQTTDeserializePublish.c\
	paho.mqtt.embedded-c/MQTTPacket/src/MQTTFormat.c\
	paho.mqtt.embedded-c/MQTTPacket/src/MQTTPacket.c\
	paho.mqtt.embedded-c/MQTTPacket/src/MQTTSerializePublish.c\
	paho.mqtt.embedded-c/MQTTPacket/src/MQTTSubscribeClient.c\
	paho.mqtt.embedded-c/MQTTPacket/src/MQTTUnsubscribeClient.c
SRCS += paho.mqtt.embedded-c/MQTTClient-C/src/MQTTClient.c

OBJS = $(SRCS:.c=.o)

.PHONEY = all clean

CFLAGS += -DMQTTCLIENT_PLATFORM_HEADER="mqtt_noos_support.h"

LIBRARY = libmqtt_client.a

all: $(LIBRARY)

$(LIBRARY): $(OBJS)
	$(AR) $(ARFLAGS) $@ $(OBJS)

clean:
	-$(call remove_fun,$(OBJS) $(LIBRARY))
