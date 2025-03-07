# prompt_RAG

## Retrieval 측면

- **Full Text**  
  - **장점:**  
    - 답변을 포함하고 있는 문서를 가져올 가능성이 매우 높음  
    - 정확도 증가  
  - **단점:**  
    - 토큰 리밋이 있어 텍스트가 너무 길면 처리 불가  
    - 같은 문서를 계속 넣을 경우 비용 증가

- **Splitted Text**  
  - **장점:**  
    - 불필요한 문서 배제  
  - **단점:**  
    - 카테고리만으로 질문과 유사한 태그를 찾을 수 없는 경우 있음  
    - 답변을 포함하고 있는 태그를 가져오지 못할 경우 정확도 감소

- **고려해야 할 것들:**  
  - 점수 기준을 낮춰 조금 더 많은 문서를 포함하도록 해야 하는지 검토 (현재 80점 기준)  
  - 카테고라이징 시 해당 문서에 대한 설명이 최대한 자세하게 되어 있어야 함  
    - 단, 너무 자세하면 Full Text를 넣는 것과 다르지 않으므로 적절한 중간 단계의 카테고리 제공 필요

## Generation 측면

- **보수적인 답변**  
  - **장점:**  
    - 무조건 문서에 있는 내용만을 바탕으로 답변하므로 정확도 증가  
  - **단점:**  
    - 질문에 대한 직접적인 근거가 되지 않더라도 도움이 될 만한 내용이 제외되어 답변 생성이 불가할 수 있음

- **조금 더 자유로운 답변**  
  - **장점:**  
    - 질문과 직접적으로 일치하지 않더라도 유사한 내용을 포함해 답변을 제공하여 사용자에게 유익한 정보 제공  
  - **단점:**  
    - 환각 현상 발생 가능성 증가

- **고려해야 할 것들:**  
  - 프롬프트 조정 필요

## 전문 용어

- 용어집을 프롬프트에 함께 포함할 경우:  
  - **장점:**  
    - 보다 구체적이고 domain에 맞는 답변 생성 가능  
  - **추가 고려 사항:**  
    - 용어집의 내용이 방대할 경우, 문서와 함께 카테고리별로 나누어 가져오는 방법 고려

## 이미지

- 문서와 마찬가지로 태그를 달고,  
- 해당 이미지에 대한 구체적인 설명이 담긴 문서를 함께 넣어주면 성능 향상