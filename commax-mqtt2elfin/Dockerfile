FROM python:3.8-alpine3.10
  
ENV LANG C.UTF-8
ENV TZ=Asia/Seoul

# update apk repo
RUN echo "http://dl-4.alpinelinux.org/alpine/v3.10/main" >> /etc/apk/repositories && \
    echo "http://dl-4.alpinelinux.org/alpine/v3.10/community" >> /etc/apk/repositories

# install chromedriver
RUN apk update && apk add chromium chromium-chromedriver

# upgrade pip
RUN pip install --upgrade pip
# Install requirements for add-on
RUN pip install paho-mqtt selenium

# Copy data for add-on
COPY run.sh /
COPY pycommax /pycommax

WORKDIR /share

RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
