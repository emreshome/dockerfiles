FROM fedora

RUN dnf -y update && dnf clean all
RUN dnf -y install initscripts xorg-x11-server-Xvfb wget git tar gzip java java-devel && dnf clean all

# set JAVA_HOME
ENV JAVA_HOME /usr/lib/jvm/java-openjdk

# set installed Maven version
ENV MAVEN_VERSION 3.2.5

# Download and install Maven
RUN curl -sSL http://archive.apache.org/dist/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz | tar xzf - -C /usr/share \
&& mv /usr/share/apache-maven-$MAVEN_VERSION /usr/share/maven \
&& ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

# Download an install Firefox
RUN wget http://rpmfind.net/linux/fedora/linux/releases/25/Everything/x86_64/os/Packages/f/firefox-49.0-2.fc25.x86_64.rpm && dnf -y install firefox-49.0-2.fc25.x86_64.rpm && dnf clean all

#Download and install geckodriver
RUN wget https://github.com/mozilla/geckodriver/releases/download/v0.18.0/geckodriver-v0.18.0-linux64.tar.gz \
&& tar -xvzf geckodriver* && chmod +x geckodriver && mv geckodriver /usr/local/bin/


RUN dnf -y --nogpgcheck install https://dl.google.com/linux/direct/google-chrome-stable_current_x86_64.rpm

ENV M2_HOME /usr/share/maven