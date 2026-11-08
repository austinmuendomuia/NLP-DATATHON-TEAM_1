# DATA_PLAN.md

Strathmore NLP Hub Datathon 2026

**Version 4.** Revised on Sunday 8 November 2026. The team has two members and uses an outside Kamba language reviewer. This version replaces the earlier plans.

## 1. Team and task

| Field | Value |
|---|---|
| Team number | 1 |
| Track | B: sentiment analysis |
| Language | Kamba (ISO 639-3: kam), language code in data: `kam-KE` |
| Kamba variety | Kitui Kamba |
| Labels | `positive`, `negative`, `neutral` |
| Unit of annotation | One sentence, one declared target |
| Final submission deadline | Wednesday 11 November 2026, 11:59 p.m. EAT |

Items marked TO CONFIRM are decided and recorded here by committing an updated version.

## 2. People and roles

| Person | Role | Code |
|---|---|---|
| Ian | Author, data documentation lead, coordinator | T01-A |
| Austin | Author, code, model and demo lead, coordinator | T01-B |
| Outside Kamba reviewer | Independent language reviewer (Kitui Kamba) | T01-R |

- Ian and Austin write the sentences and keep the source log, the model, the demo and the documents.
- The outside reviewer is a fluent Kitui Kamba speaker who is not a team member. They check every test record and a large sample of the other records for naturalness and label. Their identity is kept private; only the code `T01-R` appears in the data and documents.
- **Language competence (to be stated truthfully in the dataset card):** [TO CONFIRM: each author's connection to Kitui Kamba, for example first language, spoken at home, and any limits.]
- The organisers (Kevin and Titus) have been or will be told that the team has two members and uses an outside reviewer. Their reply is kept. The team does not lower any target on its own.

## 3. Domain and target

- **Domain:** [TO CONFIRM: one domain the authors and reviewer can speak about naturally. Candidate: campus Wi-Fi feedback.]
- **Target of opinion:** [TO CONFIRM, for example "the campus Wi-Fi service"].
- Every sentence is labelled only for the opinion it expresses toward this target. One domain and one target for the whole dataset.
- Write what a Kitui Kamba speaker would naturally say in a real situation. Do not translate English sentences word for word.

## 4. Source method

- **source_method:** `original_human`.
- **source_dataset:** `team_authored`, **source_version:** `v1`, **source_url:** `not_applicable`.
- **licence_or_permission:** `documented_contributor_permission`. Each author, and the reviewer for any wording they supply, gives written permission (a signed note or a saved message) for the sentences to be used in the datathon and the NLP Hub review. The evidence is kept in a private folder, not in the public repository.
- Kamba is not covered by AfriSenti. No external dataset is used and none counts toward the contribution target.
- No machine translation. No AI-generated sentences. AI may be used for code and explanations only and will be declared in the contribution and AI-use statement.
- Sentences contain no names, phone numbers, admission numbers or other personal details.

## 5. Labels and annotation rules

| Label | Use when |
|---|---|
| `positive` | The sentence expresses approval of the target. |
| `negative` | The sentence expresses disapproval of the target. |
| `neutral` | The sentence states a fact or asks something without a clear opinion. |

Details are in `ANNOTATION_GUIDE.md`. In short:
- Read the whole sentence. Negation can reverse meaning. Do not label from one favourable or unfavourable word.
- Exclude mixed opinion, sarcasm and unclear targets, and record each in the Exclusion Log with a reason.
- Include on purpose: minimal pairs (same words, opposite label), negation, neutral sentences that contain evaluative words, and opinions with no obvious sentiment word.
- Vary length, word order and vocabulary. No template swapping.
- Keep original spelling and diacritics. Record genuine code-switching in the `code_switching` column.

## 6. Dataset size and splits

| Label | Train | Dev | Test | Total |
|---|---|---|---|---|
| positive | 60 | 20 | 20 | 100 |
| negative | 60 | 20 | 20 | 100 |
| neutral | 60 | 20 | 20 | 100 |
| **Total** | 180 | 60 | 60 | **300** |

- Minimum is 300 accepted records. A few extra are written so weak records can be dropped during review.
- **Grouping:** minimal pairs, paraphrases and sentences built from the same idea share a `group_id` and stay in one split.
- Test data is used once, after the model, data and settings are frozen.

## 7. Authorship and independent review

- Ian (T01-A) and Austin (T01-B) each write about half of the records, with about 30 of the 60 test records each (10 per label).
- **Every test record is reviewed by the outside reviewer (T01-R).** `reviewer_code` is `T01-R` and `review_status` is `independently_reviewed`.
- The outside reviewer also reviews at least 50 percent of the train and dev records, or all of them if time allows. Records not reviewed are marked `self_reviewed`.
- If the reviewer corrects or rewrites a sentence, the corrected wording is used. The original and the correction are recorded in the Review Log with the reason, and the source log notes the change in `adjudication_note`.
- Where the reviewer judges a sentence unnatural or its label unclear, it is excluded and logged rather than forced.
- The two team members do not review each other's Kamba as a substitute for the outside reviewer, and do not mark a record `independently_reviewed` unless the outside reviewer actually reviewed it.
- If the reviewer cannot finish all test records, this is raised with the organisers at once and recorded honestly.

## 8. Source log

- **File:** `data/Kamba_Source_Log.xlsx` in the repository, with a shared working copy in Google Drive. The repository copy is updated at the data freeze.
- **One row per accepted sentence.** It records `record_id`, `text`, `label`, `contributor_code`, `reviewer_code`, `review_status`, `group_id`, `split`, `variant` (original, minimal_pair, paraphrase, translation), `adjudication_note`, plus `english_gloss` and `code_switching` as helper columns.
- **Record IDs:** `T01-A-001` for Ian's records and `T01-B-001` for Austin's.
- **Companion sheets:** Groups, Tally, Exclusion Log, Review Log.
- **Export:** columns A to Q only, saved as UTF-8 CSV to `data/contribution.csv` after the data freeze, with no `pending_review` rows.

## 9. Dates and meetings

| Date (EAT) | Milestone |
|---|---|
| Sun 8 Nov | Confirm the reviewer, permission, domain and the organisers' reply. First writing session. Meeting at 8:00 pm to check counts and balance (about 25 per label each). |
| Mon 9 Nov | Finish writing by 1:00 pm (meeting). Reviewer checks test records and a sample of the rest, 1:00 to 6:00 pm. Data freeze meeting at 9:00 pm. |
| Tue 10 Nov | Dev experiments, code freeze at noon, one final test run at 1:00 pm. Results meeting at 2:00 pm. Demo, recording and documents. Dry run at 8:00 pm. |
| Wed 11 Nov | Final check at 10:00 am. Tag `submission-v1`, record the full commit SHA, make the ZIP. Submit by 6:00 pm. |

If the data is not ready by Monday 9:00 pm, the freeze may slip to Tuesday 9:00 am at most. The reviewer's time is the main limit, so write and send records in batches rather than all at the end.

## 10. Quality and integrity commitments

- No practice rows count as contribution. No unchanged downloads are used.
- Test data is not used for tuning. Dev results are never reported as test results. No scores are invented.
- Disputed or unclear-rights records are quarantined and noted, not hidden.
- The demo uses the trained model on new input. It states the detected opinion and shows an uncalibrated probability. It does not answer the text.
- The model is compared with a majority-class baseline. A challenge set (negation, neutral sentences with evaluative words, opinions without obvious sentiment words), 15 cases written by each author and checked by the reviewer, is reported separately and never used for training.
- The dataset card states the limitations: two authors, one outside reviewer, one variety (Kitui Kamba), one domain.

## 11. Open decisions

- [ ] Reviewer confirmed, with the hours they can give before Monday evening: ________
- [ ] Written permission from each author and the reviewer recorded privately: ________
- [ ] Organisers informed and reply recorded: ________
- [ ] Language competence of each author in Kitui Kamba described: ________
- [ ] Domain and target confirmed: ________
- [ ] Private evidence folder location (not in the repo): ________

## 12. Attribution

Built from the Strathmore NLP Datathon 2026 Starter Kit v2.0 and handbook. The Kamba data is written by the two team members and reviewed by an outside fluent Kitui Kamba speaker.
