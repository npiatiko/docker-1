FROM ruby
ONBUILD COPY app /opt/app
ONBUILD WORKDIR /opt/app
RUN \
	curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - && \
	echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list && \
	apt update && \
	apt -y upgrade && \
	apt install -y nodejs yarn && \
	gem install rails
ONBUILD RUN bundle install &&\
	rake db:migrate && \
	rake db:seed
CMD bash
#docker run --rm -p 3000:3000 -ti -v app:/opt/app ft_rails