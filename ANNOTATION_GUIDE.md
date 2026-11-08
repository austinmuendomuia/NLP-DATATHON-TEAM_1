# ANNOTATION_GUIDE.md (v0)

Team 1 | Track B: sentiment analysis | Language: Kamba | Domain: campus Wi-Fi feedback

**Status:** draft v0. It is revised after Meeting 2 (review of the 30 samples) and locked as v1. Kamba examples are added by Member 3 (Language Review). The English examples below only show the rule. Do not translate them word for word into Kamba. Write what a Kamba speaker would naturally say.

## 1. What we label

- **One sentence, one target.** The target is the campus Wi-Fi service (speed, reliability, coverage, support). Label only the opinion expressed about that target.
- Three labels: `positive`, `negative`, `neutral`.
- Read the whole sentence before labelling. Never label from one favourable or unfavourable word.

## 2. Label definitions

| Label | Definition | English illustration (rule only) |
|---|---|---|
| `positive` | Approval of the target. | "The Wi-Fi in the library finally works well." |
| `negative` | Disapproval of the target. | "The Wi-Fi drops every time I open a video." |
| `neutral` | A fact, an instruction or a question with no clear opinion. | "The Wi-Fi password is on the notice board." |

## 3. Rules that stop the model learning keywords

1. **Negation changes the label.** "The Wi-Fi is good" is positive. "The Wi-Fi is not good" is negative. Read negation in Kamba as the language marks it, not as English does.
2. **Negated negatives.** "It is not bad" is mildly positive only if the speaker clearly means approval. If unclear, exclude it.
3. **Neutral sentences may contain evaluative words.** A question or a report does not express an opinion: "Is the Wi-Fi good in the hostels?" or "He said the Wi-Fi was bad" (a report of someone else's view, not the speaker's). These are neutral.
4. **Opinion without an obvious opinion word.** Describing a result or consequence can carry sentiment: "I finished my upload in two minutes" (positive), "I had to go to town to submit my assignment" (negative, if the Wi-Fi is clearly the cause). Only include these when the target and opinion are clear.
5. **Minimal pairs.** Write the same sentence with the opposite label, and give both the same `group_id`. Every group stays in one split.
6. **No template swapping.** Do not make many sentences by changing one word, name or place. Vary length, word order and vocabulary.
7. **One speaker's view.** Label the speaker's own opinion, not a quoted opinion.

## 4. Exclude and log

Do not put these in the Source Log. Record them in the Exclusion Log with a reason code:

| Reason | Meaning |
|---|---|
| `mixed_opinion` | Positive and negative in one sentence ("Fast in the library but terrible in the hostel"). |
| `sarcasm` | The literal words say the opposite of the meaning. |
| `unclear_target` | It is not clear the opinion is about the campus Wi-Fi. |
| `unnatural_kamba` | A Kamba reviewer judges it not something a speaker would say. |
| `duplicate` | The same sentence as another record. |
| `personal_detail` | Contains a name, phone number or admission number. |
| `rights_unclear` | We cannot show the author gave permission. |
| `wrong_domain` | Not about campus Wi-Fi. |

When in doubt, exclude and log. A logged exclusion is part of the contribution.

## 5. Language rules (Member 3 to complete)

- Kamba variety: ________ (set at Meeting 1)
- Spelling conventions and diacritics: keep as written. Any normalisation is documented here.
- Code-switching: record genuine Swahili or English mixing in the `code_switching` column. Do not treat it as an error.
- How approval, disapproval and "no opinion" are normally expressed in Kamba: ________
- How negation is formed and which forms are easy to miss: ________
- Expressions that are ambiguous or usually sarcastic (always exclude): ________

## 6. Worked Kamba examples (Member 3 to add; 3 or 4 per label)

| Kamba sentence | English gloss | Label | Why |
|---|---|---|---|
| | | positive | |
| | | negative | |
| | | neutral | |
| | | negative (negation) | |
| | | neutral (contains an evaluative word) | |
| | | exclude (mixed or sarcastic) | |

## 7. Process

1. Write the sentence. Add it to the Source Log with label, contributor code, `group_id`, variant and split.
2. Test records are reviewed by a different member (Member 3). The reviewer checks naturalness and label.
3. Disagreements and corrections go in the Review Log with the original value, new value and reason.
4. If a rule here is unclear, raise it at the next meeting and update this guide. Do not decide silently.

## 8. Privacy and AI

- No names, phone numbers or admission numbers in any sentence.
- Sentences are written by people. No machine translation. No AI-generated sentences.
