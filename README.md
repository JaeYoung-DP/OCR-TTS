# OCR-TTS
시각 장애인을 위한 OCR 기반 독서 보조 시스템 (OCR-based Reading Assistance System for the Visually Disabled)

> POLARIS SIF 2024 중앙대학교 차세대반도체혁신공유단 - 장려상

-  -  -

#### Train (DBNet)

```
CUDA_VISIBLE_DEVICES=0 python tools/train.py configs/textdet/dbnet/dbnet_resnet50-dcnv2_fpnc_1200e_icdar2015.py --work-dir () 
```

#### Train (ABINet)
```
CUDA_VISIBLE_DEVICES=0 python tools/train.py configs/textrecog/abinet/abinet_20e_st-an_mj.py --work-dir () 
```

#### Test (DBNet) - ( test_result의 이미지는 test의 일부입니다 ) 
```
CUDA_VISIBLE_DEVICES=0 python tools/test.py configs/textdet/dbnet/dbnet_resnet50-dcnv2_fpnc_1200e_icdar2015.py dbnet.pth --work-dir () --show-dir ()  
```

#### Test (ABINet) - (test_result의 결과는 char,sentence가 아닌 word 에서만 진행하였습니다)
```
CUDA_VISIBLE_DEVICES=0 python tools/test.py configs/textrecog/abinet/abinet_20e_st-an_mj.py abinet.pth --work-dir()
```
- - - 

## 성능 결과

<table>
  <tr>
    <th>Method</th>
    <th>Matrix</th>
    <th>Precision</th>
    <th>Recall</th>
    <th>H-mean</th>
    <th>Word_Acc</th>
  </tr>
  <tr>
    <td>DBNet</td>
    <td>-</td>
    <td>0.8723</td>
    <td>0.9102</td>
    <td>0.8909</td>
    <td>-</td>
  </tr>
  <tr>
    <td>ABINet</td>
    <td>Word_Acc</td>
    <td>-</td>
    <td>-</td>
    <td>-</td>
    <td>0.8400</td>
  </tr>
</table>




-  -  -

--wait-time 인자를 통해 대기시간을 알 수 있습니다. ( 시각화 간격(초), 기본값은 2초입니다. 기본값 설정 가능 o ) (fps 성능 확인)  


-  -  -

해당 프로젝트에서 사용되는 configs파일명은 icdar2015로 표기되지만 구동되는 내용은 ocr로 변경되었습니다.

.pth 파일인 가중치는 따로 제공하지 않습니다!





















해당 프로젝트는 MMOCR-DBNet, ABINet gTTS(google Text-to-Speech) 를 응용하여 제작되었습니다.

참조 : https://mmocr.readthedocs.io/en/dev-1.x/user_guides/train_test.html

참조 : https://gtts.readthedocs.io/en/latest/
