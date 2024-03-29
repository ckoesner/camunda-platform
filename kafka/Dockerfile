FROM confluentinc/cp-kafka:5.5.1

CMD usr/bin/kafka-configs --bootstrap-server kafka:9092 --alter --entity-type topics --entity-name __transaction_state --add-config min.insync.replicas=1