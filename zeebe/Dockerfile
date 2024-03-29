FROM maven:alpine as build
ENV HOME=/usr/app
ARG github_token
ENV ENV_GITHUB_TOKEN=$github_token

RUN mkdir -p $HOME
WORKDIR $HOME
ADD settings.xml $HOME
RUN mvn -Dtoken=${ENV_GITHUB_TOKEN} --settings $HOME/settings.xml dependency:copy -Dartifact=at.phactum.zeebe:zeebe-kafka-exporter:4.0.0:jar:jar-with-dependencies -DoutputDirectory=$HOME -P github


FROM camunda/zeebe:8.4.4
COPY --from=build /usr/app/zeebe-kafka-exporter-4.0.0-jar-with-dependencies.jar /usr/local/zeebe/exporters/zeebe-kafka-exporter.jar