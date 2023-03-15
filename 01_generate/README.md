


Command:

```
--extra-files "Transformer_model/config.json,./setup_config.json,./Seq_classification_artifacts/index_to_name.json"
```

```
torch-model-archiver \
--model-name bert \
--version 1.0 \
--serialized-file model/pytorch_model.bin \
--handler torchserve_handler.py \
--extra-files "index_to_name.json,config.json,model/tokenizer_config.json,model/special_tokens_map.json,model/vocab.txt"
```


```
podman build -t ts:01 .
podman run -it --rm --net=host ts:01
```

```
curl http://localhost:8081/models
curl -X POST http://127.0.0.1:8080/predictions/bert -T sample_text.txt
curl -X POST http://127.0.0.1:8080/explanations/bert -T  sample_text.txt
curl -d "data=I am mad at you." -X POST http://127.0.0.1:8080/predictions/bert
```