FROM python:3.10-slim

# Install system dependencies for Jupyter
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Create user for Binder
ARG NB_USER=jovyan
ARG NB_UID=1000
ENV USER=${NB_USER}
ENV HOME=/home/${NB_USER}

RUN adduser --disabled-password \
    --gecos "Default user" \
    --uid ${NB_UID} \
    ${NB_USER}

WORKDIR ${HOME}

# Install Jupyter and dependencies
COPY requirements.txt /tmp/requirements.txt
RUN pip install --no-cache-dir \
    jupyterlab \
    notebook \
    && pip install --no-cache-dir -r /tmp/requirements.txt

# Copy notebooks
COPY --chown=${NB_USER}:${NB_USER} . ${HOME}

USER ${NB_USER}

# Binder expects this
EXPOSE 8888
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--no-browser"]
