# aisecurity


graph TD
    %% 스타일 정의
    classDef ui fillcite: #e1f5fe,strokecite: #01579b,stroke-widthcite: 2px,rxcite: 10,rycite: 10;
    classDef security fillcite: #ffccbc,strokecite: #d84315,stroke-widthcite: 2px,rxcite: 10,rycite: 10;
    classDef brain fillcite: #e8f5e9,strokecite: #2e7d32,stroke-widthcite: 2px,rxcite: 10,rycite: 10;
    classDef component fillcite: #fff9c4,strokecite: #fbc02d,stroke-widthcite: 2px,rxcite: 10,rycite: 10;
    classDef observable fillcite: #f3e5f5,strokecite: #7b1fa2,stroke-widthcite: 2px,rxcite: 10,rycite: 10;

    %% 노드 정의
    UI:::ui
    
    Security:::security
    
    Agent:::brain
    
    Memory:::component
    
    Tools:::component
    
    LLM:::brain

    Observability:::observable

    %% 연결선 (흐름)
    UI -->|1. 입력| Security
    Security -->|2. 필터링된 프롬프트| Agent
    
    Agent -->|3. 지식 검색 요청| Memory
    Memory -->|4. 컨텍스트 (RAG)| Agent
    
    Agent -->|5. 도구 사용 지시| Tools
    Tools -->|6. 도구 실행 결과| Agent
    
    Agent -->|7. 전체 컨텍스트 전달| LLM
    LLM -->|8. 답변 생성| Agent
    
    Agent -->|9. 생성된 응답| Security
    Security -->|10. 최종 응답| UI
    
    Agent -.->|감사 및 모니터링| Observability
