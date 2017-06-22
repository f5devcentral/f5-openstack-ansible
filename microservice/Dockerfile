############################################################
# Dockerfile to build ansible microservice (for test, etc.)
# Based on Debian Linux, solely for an ansible service
############################################################

# The image that is produced by this Dockerfile is intended to be easily
# analyzed.  In particular all installed software is pinned to a specific
# version.  Where I knew how to do so I pinned to a checksum (commit hash) of
# the installed code.  I did not immediately know how to do this with the apt
# packages.
# Improvements:  
# If we fixed this bug:
# https://github.com/docker-library/python/issues/155
# then we could migrate to an Alpine based image,
# for the moment I'm using debian.  Probably we should fix the bug in shutil
# so that it work with Python 3.6-alpine
# Start with an awesome, debian Linux distro, with Python3 compiled in!
# NOTE: When I wrote this file the below FROM image referenced this Dockerfile:
# https://github.com/docker-library/python/blob/1ca4a57b20a2f66328e5ef72df866f701c0cd306/3.6/slim/Dockerfile
FROM    python:5cc7677d4e5c

LABEL   maintainer "za@f5.com, p.breaux@f5.com"

ENV     IMAGE_NAME ansible_microservice

#Add libraries to compile ansible
RUN     apt update
RUN     apt install -y git=1:2.1.4-2.1+deb8u3 \
                       build-essential=11.7 \
                       libssl-dev=1.0.1t-1+deb8u6 \
                       libffi-dev=3.1-2+b2 \
                       python3-dev=3.4.2-2

# Add python requirements, in base-to-dependent order.
RUN \
pip install git+git://github.com/kjd/idna@0088bfce9c3270e15d8356f0709110c1 && \
pip install git+git://github.com/wbond/asn1crypto@eff254fba6519fadb3cded95 && \
pip install git+git://github.com/benjaminp/six.git@c3ec058bf8c4d6329224eac && \
pip install git+git://github.com/eliben/pycparser.git@2b96ddfd27ec2a9ef84c && \
pip install https://bitbucket.org/cffi/cffi/get/e7063ce.tar.bz2 && \
pip install git+git://github.com/etingof/pyasn1.git@c22b813b9251c35347eace && \
pip install git+git://github.com/pyca/pynacl.git@74ef3bac181fde4bc08f5aa98 && \
pip install git+git://github.com/pyca/bcrypt.git@f3280bda0a560fbf4d401bd8e && \
pip install git+git://github.com/pyca/cryptography.git@23ead43fd70df178289 && \
pip install git+git://github.com/pallets/jinja.git@d78a1b079cd985eea7d636f && \
pip install git+git://github.com/yaml/pyyaml.git@7e026bfee9cc0bddeb1bbca0c && \
pip install git+git://github.com/paramiko/paramiko.git@353e628d34d2ffab6bf && \
pip install git+git://github.com/dlitz/pycrypto.git@af058ee6f5da391a052754 && \
git clone https://github.com/pypa/setuptools.git && cd ./setuptools && \
git checkout bf558e8d1f402c3ac9be74b96bb2002875e725 && \
python ./bootstrap.py && pip install . && cd .. && \
pip install \
git+git://github.com/ansible/ansible.git@ecb38fdf73a0beb89e9505157a2ea20c96f666
