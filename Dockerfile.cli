FROM python:3.10-slim-bullseye

# Prepare

RUN --mount=type=cache,target=/var/cache/apt,sharing=locked \
    apt-get update ; \
    apt-get upgrade -y ; \
    apt-get install -y --no-install-recommends build-essential cmake g++ ffmpeg python3 python3-pip python3-dev 
# ninja-build make gcc
    
    
RUN mkdir /gpt4all

# Build backend

COPY gpt4all-backend /gpt4all/gpt4all-backend
RUN mkdir /gpt4all/gpt4all-backend/build
WORKDIR /gpt4all/gpt4all-backend/build
RUN cmake ..
RUN cmake --build . --parallel

# Confirm that libllmodel.* exists in gpt4all-backend/build.

# Build python bindings
RUN mkdir /gpt4all/gpt4all-bindings
COPY gpt4all-bindings/python /gpt4all/gpt4all-bindings/python
WORKDIR /gpt4all/gpt4all-bindings/python
RUN --mount=type=cache,target=/root/.cache/pip,sharing=locked \
    pip install --upgrade pip && \
    pip install -e .

# Prepare, copy and execute cli

RUN --mount=type=cache,target=/root/.cache/pip,sharing=locked \
    pip install --upgrade pip && \
    pip install typer
    
RUN mkdir /cli
WORKDIR /cli
COPY gpt4all-bindings/cli/app.py .

ENTRYPOINT ["python3", "app.py"]

