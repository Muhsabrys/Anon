# EasyAnnotation: Multilingual NLI Annotation Guide

## Machine-Translated Natural Language Inference Annotation Task

**EasyAnnotation** is a framework for multilingual Natural Language Inference (NLI) annotation. It is designed to help annotators classify machine-translated sentence pairs consistently across languages.

This task investigates whether inference relations transfer across languages after machine translation from English. In most cases, annotators should choose one of three core NLI labels: **Entailment**, **Contradiction**, or **Neutral**. In rare cases, when a machine-translated sentence is broken, incomplete, or impossible to interpret, annotators may select **Nonsense**.

The **Nonsense** label should be used sparingly. If a sentence pair can still be interpreted meaningfully, even if the translation is awkward or semantically shifted, choose the logical relation instead.

---

## 1. What Is Natural Language Inference?

Natural Language Inference (NLI) is a task in natural language understanding that evaluates the logical relationship between two statements:

| Component | Definition |
| --- | --- |
| **Premise (P)** | The statement accepted as true. It provides the factual basis for reasoning. |
| **Hypothesis (H)** | The statement whose truth is evaluated relative to the premise. |

The goal is to decide whether the hypothesis follows from, contradicts, or remains undetermined by the premise.

NLI is central to many natural language processing applications, including fact-checking, question answering, reading comprehension, summarization, and dialogue systems. A model that handles NLI well can reason more coherently about meaning, implication, and contradiction.

---

## 2. Annotation Labels

Each premise and hypothesis pair must be assigned one of four labels.

| Label | Definition | Logical Interpretation | Simple Test |
| --- | --- | --- | --- |
| **Entailment** | The hypothesis logically follows from the premise. | If the premise is true, the hypothesis must be true. | This is a necessary consequence. |
| **Contradiction** | The hypothesis conflicts with the premise. | If the premise is true, the hypothesis must be false. | These cannot both be true. |
| **Neutral** | The hypothesis may or may not be true. | The premise does not provide enough information. | This could be true, but we do not know. |
| **Nonsense** | The sentence pair cannot be interpreted meaningfully. | Logical evaluation is not possible. | This does not make sense as language. |

---

## 3. Core Annotation Principle

Annotate the meaning of the translated sentence pair as it appears in the target language.

Do not assume the original English meaning if the translation has changed the meaning. Your task is to judge the relationship between the translated premise and translated hypothesis.

Use **Nonsense** only when the pair is genuinely uninterpretable. If the pair is understandable, even if the translation is odd, wrong, or mismatched, choose **Entailment**, **Contradiction**, or **Neutral**.

---

## 4. Examples of Basic Inference Relations

| Premise | Hypothesis | Label | Explanation |
| --- | --- | --- | --- |
| The museum closes at 6 PM every weekday. | Visitors cannot enter the museum at 7 PM on Tuesday. | **Entailment** | Tuesday is a weekday, and a 6 PM closing time rules out visiting at 7 PM. |
| Sarah has been a vegetarian for five years. | Sarah ate meat yesterday. | **Contradiction** | Eating meat conflicts with the stated vegetarian status. |
| The company hired ten software engineers. | The company’s revenue increased this quarter. | **Neutral** | Hiring engineers may relate to future growth, but it does not prove revenue increased. |

---

## 5. Examples of Intermediate Reasoning

| Premise | Hypothesis | Label | Explanation |
| --- | --- | --- | --- |
| All participants were aged between 18 and 25. | No minors participated in the study. | **Entailment** | Participants aged 18 or older are not minors. |
| The medication should be taken twice daily with food. | The medication should be taken on an empty stomach. | **Contradiction** | “With food” and “on an empty stomach” are mutually incompatible instructions. |
| The experiment was conducted in a controlled laboratory environment. | The findings apply to real-world settings. | **Neutral** | A laboratory setting does not by itself prove or disprove real-world generalizability. |

---

## 6. Edge Cases

| Premise | Hypothesis | Label | Explanation |
| --- | --- | --- | --- |
| Either John or Mary will attend the meeting. | John will attend the meeting. | **Neutral** | The premise guarantees at least one attendee, but it does not specify John. |
| The temperature dropped below freezing last night. | Water in outdoor containers would have frozen. | **Entailment** | Below-freezing temperatures support this physical inference under ordinary conditions. |
| The restaurant serves Italian cuisine. | Sushi is available there. | **Neutral** | The premise does not state that the restaurant serves only Italian food. |

---

## 7. Multilingual Examples

### 7.1 German

| Premise | Hypothesis | Label | Explanation |
| --- | --- | --- | --- |
| Der Zug fährt jeden Morgen um 7:30 Uhr ab. | Man kann um 7:45 Uhr in den Zug einsteigen. | **Contradiction** | If the train departs at 7:30, boarding at 7:45 is incompatible with the premise. |
| Die Bibliothek hat über 100.000 Bücher. | Die Bibliothek ist sehr gut ausgestattet. | **Entailment** | Having more than 100,000 books reasonably supports the claim that the library is well equipped. |
| Das Konzert wurde wegen Regen verschoben. | Die Band war krank. | **Neutral** | The premise gives rain as the reason, but it does not tell us whether the band was sick. |

### 7.2 Arabic

| الجملة الأصلية | الافتراض | العلاقة | التفسير |
| --- | --- | --- | --- |
| الطبيب نصح المريض بالراحة التامة لمدة أسبوعين. | يجب على المريض تجنب العمل الشاق. | **تضمين (Entailment)** | الراحة التامة تستلزم تجنب العمل الشاق. |
| جميع المتاجر مغلقة يوم الجمعة. | يمكنك التسوق يوم الجمعة. | **تناقض (Contradiction)** | إغلاق جميع المتاجر يتعارض مع إمكانية التسوق. |
| الطالب يدرس الهندسة في الجامعة. | الطالب يجيد الرياضيات. | **محايد (Neutral)** | دراسة الهندسة قد ترتبط بالرياضيات، لكنها لا تثبت الإجادة بالضرورة. |

### 7.3 Spanish

| Premisa | Hipótesis | Relación | Explicación |
| --- | --- | --- | --- |
| La conferencia comienza a las 9:00. | Si llegas a las 9:15, habrás perdido el inicio. | **Entailment** | Llegar después de la hora de inicio implica perder el comienzo. |
| María es alérgica a los frutos secos. | María puede comer almendras. | **Contradiction** | Las almendras son frutos secos, por lo que la hipótesis entra en conflicto con la alergia. |
| El restaurante tiene una estrella Michelin. | La comida es cara. | **Neutral** | La estrella puede sugerir calidad, pero no determina necesariamente el precio. |

### 7.4 Portuguese

| Premissa | Hipótese | Relação | Explicação |
| --- | --- | --- | --- |
| Todos os alunos passaram no exame. | Nenhum aluno reprovou. | **Entailment** | Se todos passaram, então nenhum aluno reprovou. |
| O voo decola às 14h. | O voo já decolou às 13h. | **Contradiction** | A hipótese contradiz o horário de decolagem informado. |
| A empresa lançou um novo produto. | As vendas vão aumentar. | **Neutral** | O lançamento pode afetar vendas, mas não garante aumento. |

### 7.5 Chinese

| 前提 | 假设 | 关系 | 说明 |
| --- | --- | --- | --- |
| 这家商店每天营业到晚上10点。 | 你可以在晚上11点购物。 | **矛盾 (Contradiction)** | 商店晚上10点关门，因此晚上11点购物与前提冲突。 |
| 所有参赛者都必须年满18岁。 | 未成年人不能参加比赛。 | **蕴含 (Entailment)** | 年满18岁的要求排除了未成年人。 |
| 这部电影获得奥斯卡奖。 | 每个人都喜欢这部电影。 | **中性 (Neutral)** | 获奖并不意味着每个人都喜欢它。 |

---

## 8. When to Use Nonsense

Use **Nonsense** only when the sentence pair cannot be evaluated because one or both sentences are not meaningful.

Examples include:

- Machine translation output that is unreadable.
- Incomplete or truncated sentences.
- Random strings with no coherent meaning.
- Severe grammatical or semantic corruption that prevents interpretation.

Do **not** use **Nonsense** just because the translation is awkward. If the sentence pair still makes sense, annotate the logical relation.

---

## 9. When to Annotate Normally

Annotate normally when both sentences are interpretable.

| Premise | Hypothesis | Label | Explanation |
| --- | --- | --- | --- |
| She sang Happy Birthday. | She sang the birthday song. | **Entailment** | The two expressions refer to the same event. |
| He hit the ball. | He hits the ball. | **Neutral** | The tense changes, so the time reference is not the same. |
| Adam Driver starred in the film. | Adam the driver starred in the film. | **Contradiction** | The mistranslation changes the meaning, but both sentences are interpretable. |

The last example should not be labeled **Nonsense**. The sentence is understandable, but its meaning has changed. Therefore, it should be judged as a logical relation.

---

## 10. Annotation Access Protocol

Each annotator receives a unique language-specific access code for the dataset assigned to them. These access codes help ensure:

- Correct language assignment.
- Controlled access to annotation data.
- Contributor accountability.
- Traceability of annotation decisions.

Access credentials are distributed directly by the project coordination team.

---

## 11. Recommended Annotation Workflow

1. Read the premise carefully.
2. Read the hypothesis carefully.
3. Ask whether the hypothesis must be true if the premise is true.
   - If yes, choose **Entailment**.
4. Ask whether the hypothesis must be false if the premise is true.
   - If yes, choose **Contradiction**.
5. Ask whether the hypothesis is possible but not guaranteed.
   - If yes, choose **Neutral**.
6. Choose **Nonsense** only if the pair cannot be interpreted meaningfully.

---

## 12. Quick Reference

| Question | Label |
| --- | --- |
| Must the hypothesis be true if the premise is true? | **Entailment** |
| Must the hypothesis be false if the premise is true? | **Contradiction** |
| Could the hypothesis be true, but we do not have enough information? | **Neutral** |
| Is the sentence pair broken or uninterpretable? | **Nonsense** |

---

## 13. Project Note

This guide is intended for multilingual NLI annotation in machine-translated datasets. The central goal is to evaluate whether inferential relations are preserved, weakened, contradicted, or made uninterpretable after translation.

 
