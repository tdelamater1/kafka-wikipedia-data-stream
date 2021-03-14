# Streaming of wikipedia events using Kafka #
This simple Python script makes use of the [EventStreams](https://wikitech.wikimedia.org/wiki/Event_Platform/EventStreams) web service which exposes a stream of structured events over HTTP following SSE protocol. Those events include information about the editing of wikipedia web pages, creation of new ones and more. For the sake of this project we filter out only the events related to the editing of existings pages. Those events are being parsed into an appropriate format and get sent back to a Kafka topic.

We construct events that are sent to Kafka with the following format:
```json
{
"id": 1426354584, 
"domain": "www.wikidata.org", 
"namespace": "main namespace", 
"title": "articles_title", 
"timestamp": "2021-03-14T21:55:14Z", 
"user_name": "a_user_name", 
"user_type": "human", 
"minor": False, 
"old_length": 6019, 
"new_length": 8687
}
```
 

### In order to reproduce this project ###
- Start a Kafka Broker at localhost:9092.
- Create a topic named **wikipedia-events**

More info on how to start up Kafka Broker create a topic, produce messages and consume them can be found [here](https://kafka.apache.org/quickstart).


- Create a Python 3 virtual environment installing all needed libraries using requirements.txt file included in this project:

```sh
python3 -m venv kafka_venv
source kafka_venv/bin/activate
pip install -r requirements.txt
```

- Εxecute the wikipedia_events_kafka_producer.py file
```sh
python wikipedia_events_kafka_producer.py 
```
