FROM fedora

RUN dnf -y update && dnf clean all
RUN dnf -y install initscripts xorg-x11-server-Xvfb wget git tar gzip bzip2 java java-devel && dnf clean all

# set JAVA_HOME
ENV JAVA_HOME /usr/lib/jvm/java-openjdk

# set installed Maven version
ENV MAVEN_VERSION 3.2.5

# Download and install Maven
RUN curl -sSL http://archive.apache.org/dist/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz | tar xzf - -C /usr/share \
&& mv /usr/share/apache-maven-$MAVEN_VERSION /usr/share/maven \
&& ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

# Download an install Firefox
RUN wget https://ftp.mozilla.org/pub/firefox/releases/56.0/linux-x86_64/en-US/firefox-56.0.tar.bz2  && tar jxf firefox-56.0.tar.bz2 -C /usr/share && ln -s /usr/share/firefox/firefox /usr/bin/firefox 

#Download and install geckodriver
RUN wget https://github.com/mozilla/geckodriver/releases/download/v0.18.0/geckodriver-v0.18.0-linux64.tar.gz \
&& tar -xvzf geckodriver* && chmod +x geckodriver && mv geckodriver /usr/local/bin/


RUN dnf -y --nogpgcheck install http://dl.google.com/linux/chrome/rpm/stable/x86_64//google-chrome-stable-65.0.3325.162-1.x86_64.rpm

ENV M2_HOME /usr/share/maven

RUN chmod -R 777 /root