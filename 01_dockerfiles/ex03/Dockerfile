FROM debian
RUN apt-get update && apt-get upgrade -y && apt-get install -y \
	curl \
	openssh-server \
	ca-certificates \
	postfix \
	nano
RUN curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash && \
	apt-get install -y gitlab-ce
RUN mkdir -p /etc/gitlab/ssl && \
	openssl req -x509 -nodes -days 365 -newkey rsa:4096 \
		-subj /CN=192.168.99.107/emailAddress=npiatiko@student.unit.ua \
		-keyout /etc/gitlab/ssl/selfsigned.key \
		-out /etc/gitlab/ssl/selfsigned.crt && \
	echo "external_url \"https://192.168.99.108\"" >> /etc/gitlab/gitlab.rb && \
	echo "nginx['redirect_http_to_https'] = true" >> /etc/gitlab/gitlab.rb && \
	echo "nginx['ssl_certificate'] = \"/etc/gitlab/ssl/selfsigned.crt\"" >> /etc/gitlab/gitlab.rb && \
	echo "nginx['ssl_certificate_key'] = \"/etc/gitlab/ssl/selfsigned.key\"" >> /etc/gitlab/gitlab.rb
ENTRYPOINT service ssh start && (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure && gitlab-ctl tail
#docker run --rm --name gitlab-ce -it -p 80:80 -p 23:22 -p 443:443 --privileged ft_git
#docker-machine create --driver virtualbox --virtualbox-memory "4096" --virtualbox-cpu-count "2" Char
