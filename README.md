[한국어](./README.md) | [English](./README_EN.md)

# Finetuning (Benchmark on subtask)

- [KoELECTRA Finetune Code](https://github.com/monologg/KoELECTRA/tree/master/finetune)를 Fork하여 제작
- Single GPU 사용

## Requirements

- python 3.9
- pip reqs

```python
torch<=1.11
transformers<5
seqeval
fastprogress
attrdict
```

## How to Run

```bash
$ python3 run_seq_cls.py --task {$TASK_NAME} --config_file {$CONFIG_FILE}
```

### KcBERT

```bash
# Base: kcbert-base.json / Large: kcbert-large.json
$ python3 run_seq_cls.py --task nsmc --config_file kcbert-base.json
$ python3 run_seq_cls.py --task kornli --config_file kcbert-base.json
$ python3 run_seq_cls.py --task paws --config_file kcbert-base.json
$ python3 run_seq_cls.py --task question-pair --config_file kcbert-base.json
$ python3 run_seq_cls.py --task korsts --config_file kcbert-base.json
$ python3 run_ner.py --task naver-ner --config_file kcbert-base.json
$ python3 run_squad.py --task korquad --config_file kcbert-base.json
```


### KcBERT-v2022

```bash
# run_all => bash run_all_kcbert_v2022.sh

python3 run_seq_cls.py --task nsmc --config_file kcbert-base-v2022.json
python3 run_seq_cls.py --task kornli --config_file kcbert-base-v2022.json
python3 run_seq_cls.py --task paws --config_file kcbert-base-v2022.json
python3 run_seq_cls.py --task question-pair --config_file kcbert-base-v2022.json
python3 run_seq_cls.py --task korsts --config_file kcbert-base-v2022.json
python3 run_ner.py --task naver-ner --config_file kcbert-base-v2022.json
python3 run_squad.py --task korquad --config_file kcbert-base-v2022.json
```


### KcELECTRA

#### Base Command

```bash
# Base: kcelectra-base.json
$ python3 run_seq_cls.py --task nsmc --config_file kcelectra-base-v1.json
$ python3 run_seq_cls.py --task kornli --config_file kcelectra-base-v1.json
$ python3 run_seq_cls.py --task paws --config_file kcelectra-base-v1.json
$ python3 run_seq_cls.py --task question-pair --config_file kcelectra-base-v1.json
$ python3 run_seq_cls.py --task korsts --config_file kcelectra-base-v1.json
$ python3 run_ner.py --task naver-ner --config_file kcelectra-base-v1.json
$ python3 run_squad.py --task korquad --config_file kcelectra-base-v1.json
```

### KcELECTRA-v2022-dev

#### Base Command

```bash
export CUDA_VISIBLE_DEVICES=1
python3 run_seq_cls.py --task nsmc --config_file kcelectra-v2022-dev.json
python3 run_seq_cls.py --task kornli --config_file kcelectra-v2022-dev.json
python3 run_seq_cls.py --task paws --config_file kcelectra-v2022-dev.json
python3 run_seq_cls.py --task question-pair --config_file kcelectra-v2022-dev.json
python3 run_seq_cls.py --task korsts --config_file kcelectra-v2022-dev.json
python3 run_ner.py --task naver-ner --config_file kcelectra-v2022-dev.json
python3 run_squad.py --task korquad --config_file kcelectra-v2022-dev.json
```

### KcELECTRA-v2022-v2-namu

#### Base Command

```bash
CUDA_VISIBLE_DEVICES=0 python3 run_seq_cls.py --task nsmc --config_file kcelectra-v2022-v2-300k-discriminator.json
CUDA_VISIBLE_DEVICES=0 python3 run_seq_cls.py --task kornli --config_file kcelectra-v2022-v2-300k-discriminator.json

CUDA_VISIBLE_DEVICES=1 python3 run_seq_cls.py --task paws --config_file kcelectra-v2022-v2-300k-discriminator.json
CUDA_VISIBLE_DEVICES=1 python3 run_seq_cls.py --task question-pair --config_file kcelectra-v2022-v2-300k-discriminator.json

CUDA_VISIBLE_DEVICES=2 python3 run_seq_cls.py --task korsts --config_file kcelectra-v2022-v2-300k-discriminator.json
CUDA_VISIBLE_DEVICES=2 python3 run_ner.py --task naver-ner --config_file kcelectra-v2022-v2-300k-discriminator.json

CUDA_VISIBLE_DEVICES=3 python3 run_squad.py --task korquad --config_file kcelectra-v2022-v2-300k-discriminator.json
```


### exKcBERT-paws

#### Command

```bash
# Base: exkcbert-paws.json
# $ python3 run_seq_cls.py --task nsmc --config_file exkcbert-paws.json
# $ python3 run_seq_cls.py --task kornli --config_file exkcbert-paws.json
$ python3 run_seq_cls.py --task paws --config_file exkcbert-paws.json
# $ python3 run_seq_cls.py --task question-pair --config_file exkcbert-paws.json
# $ python3 run_seq_cls.py --task korsts --config_file exkcbert-paws.json
# $ python3 run_ner.py --task naver-ner --config_file exkcbert-paws.json
$ python3 run_squad.py --task korquad --config_file exkcbert-paws.json
```

### exKcBERT-paws-extonly

#### Command

```bash
# Base: exkcbert-paws-extonly.json
$ python3 run_seq_cls.py --task nsmc --config_file exkcbert-paws-extonly.json
$ python3 run_seq_cls.py --task kornli --config_file exkcbert-paws-extonly.json
$ python3 run_seq_cls.py --task paws --config_file exkcbert-paws-extonly.json
$ python3 run_seq_cls.py --task question-pair --config_file exkcbert-paws-extonly.json
$ python3 run_seq_cls.py --task korsts --config_file exkcbert-paws-extonly.json
$ python3 run_ner.py --task naver-ner --config_file exkcbert-paws-extonly.json
$ python3 run_squad.py --task korquad --config_file exkcbert-paws-extonly.json
```

### exKcBERT-paws-extonly

#### Command

```bash
# Base: exkcbert-paws-extonly.json
$ python3 run_seq_cls.py --task nsmc --config_file exkcbert-paws-extonly.json
$ python3 run_seq_cls.py --task kornli --config_file exkcbert-paws-extonly.json
$ python3 run_seq_cls.py --task paws --config_file exkcbert-paws-extonly.json
$ python3 run_seq_cls.py --task question-pair --config_file exkcbert-paws-extonly.json
$ python3 run_seq_cls.py --task korsts --config_file exkcbert-paws-extonly.json
$ python3 run_ner.py --task naver-ner --config_file exkcbert-paws-extonly.json
$ python3 run_squad.py --task korquad --config_file exkcbert-paws-extonly.json
```

### exKcBERT-kowiki-extonly

#### Command

```bash
# Base: exkcbert-paws-extonly.json
$ python3 run_seq_cls.py --task nsmc --config_file exkcbert-kowiki.json
$ python3 run_seq_cls.py --task kornli --config_file exkcbert-kowiki.json
$ python3 run_seq_cls.py --task paws --config_file exkcbert-kowiki.json
$ python3 run_seq_cls.py --task question-pair --config_file exkcbert-kowiki.json
$ python3 run_seq_cls.py --task korsts --config_file exkcbert-kowiki.json
$ python3 run_ner.py --task naver-ner --config_file exkcbert-kowiki.json
$ python3 run_squad.py --task korquad --config_file exkcbert-kowiki.json
```

```
# once
python3 run_seq_cls.py --task nsmc --config_file exkcbert-kowiki.json && \
python3 run_seq_cls.py --task kornli --config_file exkcbert-kowiki.json && \
python3 run_seq_cls.py --task paws --config_file exkcbert-kowiki.json && \
python3 run_seq_cls.py --task question-pair --config_file exkcbert-kowiki.json && \
python3 run_seq_cls.py --task korsts --config_file exkcbert-kowiki.json && \
python3 run_ner.py --task naver-ner --config_file exkcbert-kowiki.json && \
python3 run_squad.py --task korquad --config_file exkcbert-kowiki.json 
```


## Result

### Base Model

|                       | Size  | **NSMC**<br/>(acc) | **Naver NER**<br/>(F1) | **PAWS**<br/>(acc) | **KorNLI**<br/>(acc) | **KorSTS**<br/>(spearman) | **Question Pair**<br/>(acc) | **KorQuaD (Dev)**<br/>(EM/F1) |
| :-------------------- | :---: | :----------------: | :--------------------: | :----------------: | :------------------: | :-----------------------: | :-------------------------: | :---------------------------: |
| exKcBERT-paws |      641M       |     n/a     |         n/a          |       TODO        |        n/a         |           n/a           |          n/a          |         TODO         |
| KcELECTRA-base |      475M       |     **91.71**      |         86.90          |       74.80        |        81.65         |           82.65           |          **95.78**          |         70.60 / 90.11         |
| KcBERT-Base                | 417M  |       89.62        |         84.34          |       66.95        |        74.85         |           75.57           |            93.93            |         60.25 / 84.39         |
| KcBERT-Large                | 1.2G  |       **90.68**        |         85.53          |       70.15        |        76.99         |           77.49           |            94.06            |         62.16 / 86.64          |
| KoBERT                | 351M  |       89.63        |         86.11          |       80.65        |        79.00         |           79.64           |            93.93            |         52.81 / 80.27         |
| XLM-Roberta-Base      | 1.03G |       89.49        |         86.26          |       82.95        |        79.92         |           79.09           |            93.53            |         64.70 / 88.94         |
| HanBERT               | 614M  |       90.16        |       **87.31**        |       82.40        |      **80.89**       |           83.33           |            94.19            |         78.74 / 92.02         |
| KoELECTRA-Base    | 423M  |     **90.21**      |         86.87          |       81.90        |        80.85         |           83.21           |            94.20            |         61.10 / 89.59         |
| KoELECTRA-Base-v2 | 423M  |       89.70        |         87.02          |     **83.90**      |        80.61         |         **84.30**         |          **94.72**          |       **84.34 / 92.58**       |
| DistilKoBERT           | 108M |       88.41        |         84.13          |       62.55        |        70.55         |           73.21           |            92.48            |         54.12 / 77.80         |


\*HanBERT의 Size는 Bert Model과 Tokenizer DB를 합친 것입니다.

\***config의 세팅을 그대로 하여 돌린 결과이며, hyperparameter tuning을 추가적으로 할 시 더 좋은 성능이 나올 수 있습니다.**

## Reference

- [Transformers Examples](https://github.com/huggingface/transformers/blob/master/examples/README.md)
- [NSMC](https://github.com/e9t/nsmc)
- [Naver NER Dataset](https://github.com/naver/nlp-challenge)
- [PAWS](https://github.com/google-research-datasets/paws)
- [KorNLI/KorSTS](https://github.com/kakaobrain/KorNLUDatasets)
- [Question Pair](https://github.com/songys/Question_pair)
- [KorQuad](https://korquad.github.io/category/1.0_KOR.html)
- [KoBERT](https://github.com/SKTBrain/KoBERT)
- [HanBERT](https://github.com/tbai2019/HanBert-54k-N)
- [HanBert Transformers](https://github.com/monologg/HanBert-Transformers)
- [KoELECTRA](https://github.com/monologg/KoELECTRA)
