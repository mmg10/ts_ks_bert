FROM docker.io/pytorch/torchserve:latest

EXPOSE 8080

EXPOSE 8081

WORKDIR /app

COPY "bert.mar" "./model_store/"

COPY "config.properties" "."

ENV ENABLE_TORCH_PROFILER=true

RUN pip install --no-cache-dir torch-tb-profiler

CMD ["torchserve", "--start", "--model-store",  "model_store", "--models", "bert=bert.mar", "--ts-config", "config.properties"]