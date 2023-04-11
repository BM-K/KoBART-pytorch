# KoBART-pytorch
🧀 KoBART summarization using pytorch + copy mechanism

## Data
- Data statistics
    - Train Data : 29,432
    - Valid Data : 7,358
    - Test Data : 9,182
 
## How to Train
- KoBART fine-tuning + Copy Mechanism
> **Warning**
> - Since the python libary was directly modified and used, I recommended to use a virtual environment. 😎
>     - geneartion_utils.py -> /site-packages/transformers/_geneartion_utils.py_
>     - modeling_bart.py -> /site-packages/transformers/models/bart/_modeling_bart.py_
- bash train_test.sh
```
[Training]
python train.py --train True --test False --batch_size 16 --max_len 512 --lr 5e-05 --epochs 10

[Testing-rouge]
python train.py --train False --test True --batch_size 16 --max_len 512
```

## Model Performance
- Test data's [rouge score](https://en.wikipedia.org/wiki/ROUGE_(metric)) 
### Base
| | rouge-1 |rouge-2|rouge-l|
|-------|--------:|--------:|--------:|
| Precision|0.5333|0.3463|0.4534|
| Recall|0.5775|0.3737|0.4869|
| F1|0.5381|0.3452|0.4555|

### Copy Mechanism
| | rouge-1 |rouge-2|rouge-l|
|-------|--------:|--------:|--------:|
| Precision|0.5698|0.3776|0.4882|
| Recall|0.5561|0.3612|0.4717|
| F1|0.5460|0.3545|0.4654|

## Examples
| | |Text|
|-------|:--------|:--------|
|1|기사|경기도와 경기도시공사는 광교원천, 동탄호수공원, 성남판교 등 3개 지구에 건립 예정인 총 730가구의 경기행복주택 입주자를 모집한다고 26일 밝혔다. 모집 기간은 다음달 2일부터 11일까지이며, ‘경기도시공사 임대주택 청약센터(https://apply.gico.or.kr)’에서 인터넷 청약접수로 진행된다. 광교원천 경기행복주택은 전용면적 16㎡형 대학생 40가구와 청년 20가구, 26㎡형 청년 186가구와 고령자 24가구, 주거급여수급자 30가구까지 총 300가구를 모집한다. 보증금 2천729만4천&#126;4천783만3천 원에 월 임대료는 11만8천&#126;20만7천 원이다. 입주 예정은 오는 2020년 11월이다. 동탄호수공원 경기행복주택은 동탄2신도시에 6개동 995가구 조성되는 대규모 단지이다. 이번 입주자 모집에서는 공급면적 44㎡형 신혼부부 130가구를 우선 모집하며 임대조건은 보증금 5천만 원에 월 임대료 20만8천 원이다. 내년 12월 입주 예정으로, 나머지 가구는 연말에 모집할 예정이다 성남판교 경기행복주택은 전용면적 16㎡형 창업인 100가구와 청년 124가구, 26㎡형 청년 46가구와 고령자 30가구 등 총 300가구를 모집하며, 보증금 3천876만&#126;6천992만 원에 월 임대료 14만5천&#126;26만2천 원이다. 김준태 도 도시주택실장은 ""도내 청년층을 주요 대상으로 한 주거복지정책인 경기행복주택은 2022년까지 1만호를 공급하는 과정에서 매년 공급물량이 늘어날 예정""이라며 ""경기행복주택 사업에도 많은 관심을 가져달라""고 말했다.|
|1|모델요약|경기도와 경기도시공사는 광교원천, 동탄호수공원, 성남판교 등 3개 지구에 건립 예정인 총 730가구의 경기행복주택 입주자를 모집한다고 26일 밝혔으며 모집 기간은 다음달 2일부터 11일까지이며, 보증금 2천729만4천&#126;4천783만3천 원에 월 임대료는 11만8천&#126;20만7천 원이다.|
|2|기사|전남개발공사, ‘일자리창출’우수기관 선정 전남개발공사 청사 전경. 전남개발공사가 일자리창출 우수기관에 선정돼 행정안전부장관 표창을 수상했다. 6일 전남개방공사에 따르면 지난 3일 세종컨벤션센터에서 열린 2019년 상반기 지방공사·공단 CEO 리더십 포럼에서 이같이 수상 했다고 밝혔다. 전남개발공사는 문재인 정부 역점 사업인 일자리창출 정책에 적극 부응하며, 지역의 고용시장 활성화하기 위해 신규사업 발굴 등에 역점을 뒀다. 이 결과 지난해 2회에 걸쳐 10명을 채용하는 등 정부의 청년 및 장애인 의무고용에 대한 기준을 충족시켰다는 평가를 받았다. 또한 지역내 사회 초년생의 안정적인 취업에 도움이 될 수 있는 양질의 일자리 경험 및 역량을 쌓을 수 있도록 전라남도가 중점 추진하고 있는 ‘청년 내일로 프로젝트’에 참여해 7명의 지역인재를 선발하기도 했다. 특히 전남개발공사의 채용은 공정성과 투명성 위해 전면 블라인드 절차에 따라 진행되며, 특히 면접은 전원 외부면접위원으로 진행된다. 올해 채용은 전반기에 2명을 채용했으며하반기에는 추가로 5명이내의 규모로 진행될 예정이다. 한편 전남개발공사는 지난 2004년 전남도가 설립한 지방공기업으로 남악신도시, 빛가람 혁신도시, 여수경도해양관광단지 개발사업 등을 시행했고, 여수 죽림지구 택지개발사업도 추진할 계획이다.|
|2|모델요약|전남개발공사는 지난 3일 세종컨벤션센터에서 열린 2019년 상반기 지방공사·공단 CEO 리더십 포럼에서 일자리창출 우수기관에 선정돼 행정안전부장관 표창을 수상했다.|
|3|기사|광주시는 지역 유망강소기업을 발굴·육성하기 위해 운영하고 있는 ‘100대 명품강소기업 육성사업’에 참가할 기업을 모집한다. 명품강소기업 육성사업은 성장 잠재력과 뛰어난 기술력을 가진 지역 중소·중견기업을 발굴해 지역경제를 견인할 글로벌 기업으로 육성하기 위한 시책으로, 2014년 시작돼 올해로 6년째를 맞았다. 모집대상은 공고일 현재 본사와 주사업장이 광주에 위치한 제조업 및 지식서비스산업 기업으로 총 30개사다. 이번 모집은 현재 제3기 명품강소기업 27개사의 지정기간(3년)이 만료됨에 따라 이들 기업의 재지정 여부와 함께 재지정 포기·탈락 기업 결원분을 채우기 위해 추진됐다. 선정조건은 명품강소기업은 매출액 50억원 이상(지식서비스산업은 10억원 이상)이면서 최근 5년 간 연평균 매출액 증가율 5% 이상이거나, 최근 3년 간 매출액 대비 R&D 투자 비율이 1% 이상인 기업이다. 명품강소기업으로 선정되면 광주시 자금 지원, 기업진단 컨설팅, 성장전략 마련, 해외마케팅 등 기업중심 맞춤형 지원과 함께 다양한 우대 혜택을 받게 된다. 또 중앙정부(중소벤처기업부)와 연계한 기업성장사다리를 통해 단계별 성장전략 지원도 받을 수 있어 명품강소기업 선정 이후 글로벌 기업으로 발돋움할 수 있을 것으로 기대된다. 신청은 31일까지 광주테크노파크로 방문 접수하면 된다. 자세한 내용은 광주시 홈페이지(http://www.gwangju.go.kr) 고시·공고란을 참고하거나 광주시 기업육성과(062-613-3871)로 문의하면 된다. 광주시는 신청기업을 대상으로 1차 서류심사, 2차 발표·현장평가를 거쳐 8월 선정위원회에서 최종 확정할 계획이다.|
|3|모델요약|광주시는 지역 중소·중견기업을 발굴해 지역경제를 견인할 글로벌 기업으로 육성하기 위해 운영하고 있는 '100대 명품강소기업 육성사업'에 참가할 기업을 모집한다.|

## Reference
- [KoBART](https://github.com/SKT-AI/KoBART)
- [KoBART-summarization](https://github.com/seujung/KoBART-summarization)

