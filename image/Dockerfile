# Copyright 2016 The Kubernetes Authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

FROM rhel7

COPY epel.repo /etc/yum.repos.d/epel.repo

COPY logrotate-3.8.6-14.el7.x86_64.rpm /tmp/

RUN yum install /tmp/logrotate-3.8.6-14.el7.x86_64.rpm -y

COPY RPM-GPG-KEY-EPEL-7 /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7

RUN yum install epel-release -y

RUN yum install redis -y

RUN yum install hostname -y

COPY redis-master.conf /redis-master/redis.conf
COPY redis-slave.conf /redis-slave/redis.conf
COPY run.sh /run.sh
RUN mkdir -p /redis-sentinel && chmod -R 777 /redis-sentinel /redis-slave 
RUN chmod 777 /run.sh

CMD [ "/run.sh" ]

ENTRYPOINT [ "bash", "-c" ]
