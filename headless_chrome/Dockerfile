From alpine:edge
LABEL maintainer="idani@exp-t.com"

RUN apk add --no-cache \
  udev \
  ttf-freefont \
  chromium \
  nodejs \
  nodejs-npm

RUN mkdir /noto

ADD https://noto-website.storage.googleapis.com/pkgs/NotoSansCJKjp-hinted.zip /noto 

WORKDIR /noto

RUN unzip NotoSansCJKjp-hinted.zip && \
    mkdir -p /usr/share/fonts/noto && \
    cp *.otf /usr/share/fonts/noto && \
    chmod 644 -R /usr/share/fonts/noto/ && \
    fc-cache -fv

WORKDIR /
RUN rm -rf /noto


ENV PUPPETEER_SKIP_CHROMIUM_DOWNLOAD true

RUN npm install \
    npm \
    puppeteer \
    express \
    connect-timeout \
    body-parser

RUN mkdir /varuna/
WORKDIR /varuna/

# COPY my app dir
COPY app app
RUN chmod -R 777 /varuna/app


EXPOSE 8000

# RUN useradd chromeuser -s /bin/bash -m -u 10000
# USER chromeuser

CMD ["node", "app/pdf-server.js"]
# ENTRYPOINT tail -f /dev/null