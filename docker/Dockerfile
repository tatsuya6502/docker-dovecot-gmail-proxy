## The MIT License
##
## Copyright (C) 2015 by Tatsuya Kawano
##
## Permission is hereby granted, free of charge, to any person obtaining a copy
## of this software and associated documentation files (the "Software"), to deal
## in the Software without restriction, including without limitation the rights
## to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
## copies of the Software, and to permit persons to whom the Software is
## furnished to do so, subject to the following conditions:
##
## The above copyright notice and this permission notice shall be included in
## all copies or substantial portions of the Software.
##
## THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
## IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
## FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
## AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
## LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
## OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
## THE SOFTWARE.

FROM centos:centos7
MAINTAINER Tatsuya Kawano

RUN (yum -y update && yum -y install dovecot)

RUN (sed -i -e 's/.*protocols =.*/protocols = imap/' /etc/dovecot/dovecot.conf && \
     sed -i -e 's/.*\(!include auth-system.*\)/#\1/' /etc/dovecot/conf.d/10-auth.conf && \
     sed -i -e 's/.*\(!include auth-static.*\)/\1/' /etc/dovecot/conf.d/10-auth.conf)
COPY ./auth-static.conf.ext /etc/dovecot/conf.d/auth-static.conf.ext

# Clean Up
RUN yum clean all

EXPOSE 993/tcp
ENTRYPOINT ["/usr/sbin/dovecot", "-F"]a

