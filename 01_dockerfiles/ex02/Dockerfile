FROM ruby

RUN apt-get -y update && \
	apt-get -y upgrade && \
    apt-get -y install build-essential libpq-dev nodejs sqlite3 rails && \
    rm -rf /var/lib/apt/lists/* && \
    apt-get clean

ONBUILD COPY app /opt/app
ONBUILD WORKDIR /opt/app
ONBUILD RUN bundle install

#runs migrations for the current env that have not run yet
ONBUILD RUN rake db:migrate

#(only) runs the db/seed.rb file
#http://www.xyzpub.com/en/ruby-on-rails/3.2/seed_rb.html
#ONBUILD RUN rake db:seed

#cp -R ~/app .
#cp ~/Dockerfile_parent .
#docker build -t ft-rails:on-build . || preciser le chemin avec -f
#docker run -it --rm ft-rails:on-build
