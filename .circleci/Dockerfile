FROM openjdk:8-jdk-alpine

RUN apk update && \
    apk upgrade && \
    apk add --no-cache bash git openssh

ENV ANDROID_SDK_URL http://dl.google.com/android/repository/sdk-tools-linux-3859397.zip
ENV ANDROID_HOME /opt/android-sdk

RUN mkdir -p ${ANDROID_HOME} && cd ${ANDROID_HOME} && \
    wget -O tools.zip ${ANDROID_SDK_URL} && \
    unzip tools.zip && rm tools.zip

ENV PATH $PATH:$ANDROID_HOME/tools
ENV PATH $PATH:$ANDROID_HOME/platform-tools

RUN echo "y" | android update sdk --no-ui --all --filter " \
              tools,android-25,build-tools-25.0.3,platform-tools, \
              extra-android-support,extra-google-m2repository,extra-google-google_play_services"

RUN echo y | $ANDROID_HOME/tools/bin/sdkmanager "extras;m2repository;com;android;support;constraint;constraint-layout-solver;1.0.2"
