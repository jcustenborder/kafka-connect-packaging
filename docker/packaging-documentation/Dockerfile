FROM python

MAINTAINER jcustenborder@gmail.com

RUN useradd --uid 1000 -m jenkins
RUN pip install sphinx sphinx-autobuild sphinx_rtd_theme
RUN apt-get update && apt-get install -y rsync
USER jenkins