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
ENV PATH /home/action/.local/bin/xbuild:$PATH
ENV AUTOPARTS_DEV true
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8
ENV LC_ALL en_US.UTF-8
ENV LC_CTYPE UTF-8
ENV LC_MESSAGES C

WORKDIR /home/action
RUN parts install \
    chruby \
    ruby2.2
RUN gem install \
    bundler \
    rails
RUN mkdir -p ~/.local/bin
RUN git clone https://github.com/tagomoris/xbuild.git ~/.local/bin/xbuild
RUN perl-install 5.18.2 ~/.local/perl-5.18
RUN yes | cpanm \
    YAML::Loader \
    XML::LibXML \
    XML::LibXML::SAX \
    XML::LibXML::XPathContext \
    XML::Liberal \
    Text::Glob \
    Module::Runtime \
    Params::Util \
    Digest::SHA1
RUN yes | cpanm -fi \
    Class::Load \
    XML::RSS \
    XML::RSS::LibXML \
    XML::RSS::Liberal \
    XML::Feed \
    XML::Feed::RSS \
    XML::Atom \
    WebService::Bloglines \
    Plagger

EXPOSE 22
CMD sudo /usr/sbin/sshd -D
