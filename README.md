# RAG-LLM
 Azərbaycan dilində düzgün cavab verən, mənbəyə əsaslanan və məntiqi sualları həll edən kiçik AI prototipi hazırlamaq.
 Google Colab-da işə salma

1. `rag_az_complete_project_updated.ipynb` faylını Google Colab-a yükləyin.

1. Hüceyrələri yuxarıdan aşağıya ardıcıl işlədin.

1. Əvvəlcə `USE_LLM = False` saxlayın və embedding/retrieval nəticələrini yoxlayın.

1. LLM testi üçün `USE_LLM = True` edin. Notebook sizdən API endpoint, API açarı və model adını istəyəcək.

1. İki modelin müqayisəsi üçün `RUN_COMPARISON = True` edin və iki model adını daxil edin.

1. Yaranan `comparison_results.csv` faylını yükləyin.

Hugging Face Token: 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 
BASE_URL https://openrouter.ai/api/v1
API_KEY: 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

Model A:
qwen/qwen3.5-9b

Model B:
google/gemma-3-4b-it


Model müqayisəsinin qiymətləndirilməsi

Tapşırıq üzrə test dəsti 15 sualdan ibarətdir:

- 5 fakt sualı;

- 5 müqayisə və hesablama sualı;

- 5 cavabı mənbədə olmayan sual.

Hər model üçün 15 sətir, ümumilikdə isə 30 nəticə sətiri gözlənilir.

Aşağıdakı sütunlar cavablar oxunduqdan sonra insan tərəfindən 0–5 arası doldurulur:

```
azerbaijani_0_5
reasoning_0_5
faithfulness_0_5
notes
```

Qiymətləndirmə meyarları:

| Bal | İzah |
| --- | --- |
| 5 | Tam düzgün, aydın və mənbəyə sadiq |
| 4 | Əsasən düzgün, kiçik çatışmazlıq var |
| 3 | Qismən düzgün |
| 2 | Əhəmiyyətli məntiqi və ya fakt xətası var |
| 1 | Çox zəif və ya əsasən səhvdir |
| 0 | Cavab yoxdur və ya tamamilə yanlışdır |


Ən yaxşı model barədə əsaslandırma

Bu layihədə qwen/qwen3.5-9b və google/gemma-3-4b-it modelləri eyni 15 sual, eyni RAG konteksti və eyni Top-3 retrieval nəticələri ilə müqayisə edilmişdir.

qwen/qwen3.5-9b orta ümumi bal üzrə 4.22/5 nəticə ilə daha yüksək nəticə göstərmişdir. Modelin Azərbaycan dili üzrə orta balı 5.00/5, reasoning üzrə orta balı 3.93/5, faktlara sadiqlik üzrə orta balı isə 3.73/5 olmuşdur. Modelin orta cavab müddəti 14.69 saniyə təşkil etmişdir. Digər model olan google/gemma-3-4b-it üçün orta ümumi bal 3.98/5 olmuşdur. Naməlum suallarda modelin məlumat uydurub-uydurmadığı faithfulness göstəricisi və manual review nəticələri ilə birlikdə nəzərə alınmışdır. Buna görə qwen/qwen3.5-9b bu 15 sintetik sual və istifadə olunan RAG konteksti üçün daha uyğun model hesab edilmişdir.
