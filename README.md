[한국어](./README.md) | [English](./README_EN.md)

# Finetuning (Benchmark on subtask)

- [Transformers examples](https://github.com/huggingface/transformers/blob/master/examples/README.md)를 참고하여 제작
- Finetuning에는 `discriminator`를 사용
- Single GPU 기준으로 코드 작성

## Updates

**July 7, 2020**

- `transformers v3`에 맞춰서 코드를 수정하였습니다. 기존에는 `ElectraForSequenceClassification` 등이 지원되지 않아 직접 구현하였지만, 최근에는 공식 라이브러리에 구현이 되어 있어서 이를 사용하는 방향으로 수정하였습니다.
- 기존 `src/model.py`에서의 `ElectraForSequenceClassification`과 [modeling_electra.py](https://github.com/huggingface/transformers/blob/master/src/transformers/modeling_electra.py)의 `ElectraForSequenceClassification` 구현 방식이 상이합니다.
  - [Result](https://github.com/monologg/KoELECTRA/blob/master/finetune/README.md#result)의 nsmc 결과는 이전 `src/model.py` 기준입니다.

## Requirements

```python
torch==1.5.1
transformers==3.0.2
seqeval
fastprogress
attrdict
```

## How to Run

```bash
$ python3 run_seq_cls.py --task {$TASK_NAME} --config_file {$CONFIG_FILE}
```

```bash
$ python3 run_seq_cls.py --task nsmc --config_file koelectra-base.json
$ python3 run_seq_cls.py --task kornli --config_file koelectra-base.json
$ python3 run_seq_cls.py --task paws --config_file koelectra-base.json
$ python3 run_seq_cls.py --task question-pair --config_file koelectra-base-v2.json
$ python3 run_seq_cls.py --task korsts --config_file koelectra-small-v2.json
$ python3 run_ner.py --task naver-ner --config_file koelectra-small.json
$ python3 run_squad.py --task korquad --config_file xlm-roberta.json
```

## Result

### Base Model

|                       | Size  | **NSMC**<br/>(acc) | **Naver NER**<br/>(F1) | **PAWS**<br/>(acc) | **KorNLI**<br/>(acc) | **KorSTS**<br/>(spearman) | **Question Pair**<br/>(acc) | **KorQuaD (Dev)**<br/>(EM/F1) |
| :-------------------- | :---: | :----------------: | :--------------------: | :----------------: | :------------------: | :-----------------------: | :-------------------------: | :---------------------------: |
| KoBERT                | 351M  |       89.63        |         86.11          |       80.65        |        79.00         |           79.64           |            93.93            |         52.81 / 80.27         |
| XLM-Roberta-Base      | 1.03G |       89.49        |         86.26          |       82.95        |        79.92         |           79.09           |            93.53            |         64.70 / 88.94         |
| HanBERT               | 614M  |       90.16        |       **87.31**        |       82.40        |      **80.89**       |           83.33           |            94.19            |         78.74 / 92.02         |
| **KoELECTRA-Base**    | 423M  |     **90.21**      |         86.87          |       81.90        |        80.85         |           83.21           |            94.20            |         61.10 / 89.59         |
| **KoELECTRA-Base-v2** | 423M  |       89.70        |         87.02          |     **83.90**      |        80.61         |         **84.30**         |          **94.72**          |       **84.34 / 92.58**       |

\*HanBERT의 Size는 Bert Model과 Tokenizer DB를 합친 것입니다.

### Small Model

|                        | Size | **NSMC**<br/>(acc) | **Naver NER**<br/>(F1) | **PAWS**<br/>(acc) | **KorNLI**<br/>(acc) | **KorSTS**<br/>(spearman) | **Question Pair**<br/>(acc) | **KorQuaD (Dev)**<br/>(EM/F1) |
| :--------------------- | :--: | :----------------: | :--------------------: | :----------------: | :------------------: | :-----------------------: | :-------------------------: | :---------------------------: |
| DistilKoBERT           | 108M |       88.41        |         84.13          |       62.55        |        70.55         |           73.21           |            92.48            |         54.12 / 77.80         |
| **KoELECTRA-Small**    | 53M  |     **88.76**      |         84.11          |       74.15        |        76.27         |           77.00           |            93.01            |         58.13 / 86.82         |
| **KoELECTRA-Small-v2** | 53M  |       88.64        |       **85.05**        |     **74.50**      |      **76.76**       |         **78.28**         |          **93.66**          |       **81.43 / 90.37**       |

\***config의 세팅을 그대로 하여 돌린 결과이며, hyperparameter tuning을 추가적으로 할 시 더 좋은 성능이 나올 수 있습니다.**

- `KoELECTRA-Base`의 경우 `KoBERT`보다 좋은 성능을 보이며, `HanBERT`와 일부 Task에서 유사한 성능을 보입니다.
- `KoELECTRA-Small`의 경우 전반적으로 `DistilKoBERT`보다 좋은 성능을 보입니다.

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
