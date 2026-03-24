FROM amd64/ubuntu:jammy
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get -qq update
RUN apt-get install -y --no-install-recommends \
    python3 python3-pip tree \
    git openssh-client texlive-latex-base texlive-xetex cm-super dvipng

# setup analysis user
RUN useradd -ms /bin/bash analysis \
 && mkdir -p /home/analysis \
 && mkdir -p /analysis \
 && chown -R analysis:analysis /home/analysis /analysis

# switch user
USER analysis
ENV PATH="/home/analysis/.local/bin:$PATH"

# install eos (and dependencies)
ARG EOS_VERSION
RUN pip3 install --user --upgrade "eoshep==$EOS_VERSION"
