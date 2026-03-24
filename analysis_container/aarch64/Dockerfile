FROM arm64v8/ubuntu:jammy
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get -qq update
RUN apt-get install -y --no-install-recommends \
    python3 python3-pip tree \
    git openssh-client texlive-latex-base texlive-xetex cm-super dvipng \
    gcc g++ python3-dev
# gcc needed to build ``psutils``, which is pulled in as a dependency by one
# of the packages we install below.

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
