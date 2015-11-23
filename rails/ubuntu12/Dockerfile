FROM quay.io/nabinno/dove-ubuntu12
USER action
ENV HOME /home/action
ENV PATH /home/action/bin::$PATH
ENV PATH /home/action/local/bin:$PATH
ENV PATH /home/action/.parts/autoparts/bin:${PATH}
ENV PATH /home/action/.gem/ruby/2.2.0/bin:$PATH
ENV PATH /home/action/.parts/opt/rubies/ruby-2.2.0/bin:$PATH
ENV PATH /home/action/.local/perl-5.18/bin:$PATH
ENV PATH /home/action/.local/bin:$PATH
ENV AUTOPARTS_DEV true

WORKDIR /home/action
RUN parts install \
    chruby \
    ruby2.2
RUN gem install \
    bundler \
    rails
RUN mkdir -p ~/.local/bin

EXPOSE 22
CMD sudo /usr/sbin/sshd -D
