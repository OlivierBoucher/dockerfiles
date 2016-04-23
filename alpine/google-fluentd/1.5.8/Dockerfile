FROM alpine:3.2

RUN apk update \
	&& apk add bash build-base ca-certificates ruby-dev \ 
	&& echo 'gem: --no-document' >> /etc/gemrc \
	&& gem install fluentd -v 0.12.22 \
	&& gem install fluent-plugin-google-cloud -v 0.5 \
	&& apk del build-base ruby-dev \
	&& rm -rf /root/.gem

ENV FLUENTD_CONF = /etc/google-fluentd/google-fluentd.conf
ENV AUTH_METHOD compute_engine_service_account
ENV PRIVATE_KEY_EMAIL some@developer.gserviceaccount.com

ADD google-fluentd.conf  /etc/google-fluentd/google-fluentd.conf

# NOTE(Olivier): Rebase and add this line when building for a certain service
# ADD config/*.conf /etc/google-fluentd/config.d/

# NOTE(Olivier): When rebasing, don't forget to copy the .p12 keyfile
# ADD keyfile.p12 /etc/google-fluentd/keyfile.p12

CMD fluentd -c $FLUENTD_CONF
