# Lesson 3 — Hands-on with Göttingen's Chat AI

Open **[chat-ai.academiccloud.de](https://chat-ai.academiccloud.de)** and log in with your university account (Academic Cloud).

For every task, write down **which model** you used and **what went wrong**.

> 🔒 **Privacy rule.** Models hosted by GWDG run in Göttingen and do not store your chats. External models (GPT, Claude) send your text to the provider (Microsoft Azure). **No personal data and no unpublished data on external models.**

## 📋 Prompt list

Each prompt is also a separate text file in [`prompts/`](prompts/): open it, copy it, paste it into Chat AI.

| Task | Prompt file | Files you need | Model |
|---|---|---|---|
| 1 · Sources | [`task1_sources.txt`](prompts/task1_sources.txt) | — | small, then big |
| 2 · Logic traps | [`task2_logic.txt`](prompts/task2_logic.txt) | — | small, then big |
| 3 · OCR | [`task3_ocr.txt`](prompts/task3_ocr.txt) | `task3_finds_register_scan.jpg` | one that sees images |
| 4 · Gänseliesel OS | [`task4_os.txt`](prompts/task4_os.txt) | — | one for code |
| 5 · A paper | [`task5_paper.txt`](prompts/task5_paper.txt) | `task5_Cardarelli_2024_JCH.pdf` | small, then big |
| 6 · The vase | [`task6_vase.txt`](prompts/task6_vase.txt) | `task6_vase.jpg` | one that sees images |
| Demo (lecturer) | [`demo_agent.txt`](prompts/demo_agent.txt) | `demo_finds_dataset.csv` | an agent |

## Which model?

| Role | First choice | If you don't see it / it doesn't work |
|---|---|---|
| **Small** model | Llama 3.1 8B Instruct (GWDG) | Qwen 3 30B A3B Instruct (GWDG) |
| **Big** model | Qwen 3.5 397B A17B (GWDG) | DeepSeek V4 Flash (GWDG) |
| **Commercial** model (paid by the university, external) | GPT-5.5 or Claude Sonnet 5 | Qwen 3.5 397B A17B (open, GWDG) |
| Model that **sees images** (tasks 3 and 6) | Qwen 3 Omni 30B A3B or Gemma 4 31B (GWDG) | GPT-5.5 (external), if available to you |
| Model for **code** (task 4) | Qwen 3 Coder Next (GWDG) | Claude Sonnet 5 (external), if available to you |

Model names change often. If a model is not in the menu, take the closest one and write down what you used.

---

## Task 1 — "Give me sources"

Ask the **small** model, then the **big** one:

```
Give me 5 peer-reviewed articles, with authors, year, journal and DOI, on computer methods (machine learning or 3D) for reconstructing ceramic vessels from sherds (fragment reassembly).
```

Check two of the references: search the title on [Google Scholar](https://scholar.google.com), or put the DOI after `https://doi.org/`.

Count how many are **real**, how many are **half-real** (a real author with an invented title, a wrong year), and how many are **invented**.

## Task 2 — Logic traps

Ask one at a time, in a new message each time:

```
How many letters 's' are in the word Varusschlacht?
```
```
Write Varusschlacht backwards.
```
```
What is 4,817 × 2,936?
```
```
What is today's date?
```
(Ask for the date again with **Tools → Web Search** switched on. This only works with GWDG models.)

And the famous one from February 2026:

```
I want to wash my car. The car wash is 50 meters away. Should I walk or drive?
```

<details><summary>Answers</summary>

- 2 letters s
- thcalhcssuraV
- 14,142,712
- the date of today's lesson
- **Drive.** The car has to be at the car wash.

</details>

## Task 3 — OCR: read a scanned table

Download [`task3_finds_register_scan.jpg`](task3_finds_register_scan.jpg). Attach it with **+** to a model that sees images, and ask:

```
This is a scanned page of a finds register. Transcribe the table exactly as CSV, one row per find, with the same columns. Do not translate. Where a value was corrected by hand, use the corrected value. Mark anything you cannot read with [?].
```

Then compare with [`task3_finds_register_SOLUTION.csv`](task3_finds_register_SOLUTION.csv): **open it only afterwards**.

## Task 4 — Gänseliesel OS

**Step 1.** Pick your style with the **last digit of your student number** (Matrikelnummer):

| Digit | Style |
|---|---|
| 0–1 | Windows 95 |
| 2–3 | classic Macintosh (1990s) |
| 4 | MS-DOS green terminal |
| 5 | Windows XP |
| 6 | Commodore 64 / 1980s home computer |
| 7 | futuristic spaceship computer |
| 8 | medieval manuscript (parchment, ink, illuminated letters) |
| 9 | a style you invent yourself |

**Step 2.** Replace `[YOUR STYLE]` in the prompt and send it, preferably to a model that is good at code:

```
Create a single HTML file (HTML, CSS and JavaScript in one file, no external libraries, no images from the internet) called "Gänseliesel OS": a fake operating system themed on the city of Göttingen, in the style of [YOUR STYLE].

Requirements:
- A boot screen ("Gänseliesel OS is starting…") and a desktop with a taskbar or menu, and a clock.
- At least 6 icons or menu entries that open windows you can move around, for example: the Gänseliesel fountain (and the tradition of kissing her after a doctorate), Gauss and Weber's telegraph (1833), Lichtenberg's aphorisms, the "Göttinger Sieben" (1837), the Nobel laureates of Göttingen, a "Mensa menu" app, a weather app where it always rains, a bike-parking app where all spaces are taken.
- Fill it with real facts about Göttingen and with jokes. Every fact must be correct.
- A FUN GAME that really works, themed on Göttingen: for example help the Gänseliesel catch her runaway geese, find a free bike parking space before the lecture starts, dodge the rain on the way to the Mensa, or a quiz on Göttingen's history. It needs a score, a way to lose or win, and a restart button.
```

**Step 3.** Save the answer as `gaenseliesel_os.html` (in Notepad choose *Save as type: All files*), then double-click it.

- **Doesn't work?** Press **F12**, copy the red error, paste it back into the chat and ask for a fix.
- **Works?** Play the game. Then check **three facts**: are the dates right?
- At the end we compare: same prompt, different styles, different models. Whose OS is the best?

## Task 5 — A paper we know well

Download [`task5_Cardarelli_2024_JCH.pdf`](task5_Cardarelli_2024_JCH.pdf). It is L. Cardarelli, "From fragments to digital wholeness: An AI generative approach to reconstructing archaeological vessels", *Journal of Cultural Heritage* 70 (2024), 250–258, [doi:10.1016/j.culher.2024.09.012](https://doi.org/10.1016/j.culher.2024.09.012), open access, CC BY 4.0.

Attach it with **+** and ask:

```
List all the archaeological sites analysed in this article, with the region and the period for each. Use only the article. If something is not in the article, say so.
```

<details><summary>The real list (open afterwards)</summary>

Six contexts (Table 1 of the article):

| Context | Period | Role |
|---|---|---|
| Casinalbo | MBA/LBA | training |
| Pianello di Genga | FBA | training |
| Osteria dell'Osa | EIA1 | training |
| Torre Galli | EIA1/EIA2 | training |
| Quattro Fontanili | EIA1/EIA2 | training |
| Narde | FBA | post-training evaluation |

MBA = Middle Bronze Age · LBA = Late Bronze Age · FBA = Final Bronze Age · EIA = Early Iron Age.

**The trap:** the **regions are not in the article.** The map is in the supplementary materials. A careful model says so. A careless one adds regions from its own memory, sometimes right and sometimes wrong.

</details>

## Task 6 — Date a vase from a photo

Download [`task6_vase.jpg`](task6_vase.jpg). Attach it to a model that sees images, and ask:

```
You are an archaeologist. From this photo only, identify the object: culture, region, date range and function. Explain which features you used, and say how sure you are.
```

<details><summary>What it is (open afterwards)</summary>

A **Villanovan biconical cinerary urn** with its bowl-lid, from **Chiusi** (Etruria), **9th–7th century BC**. Museo Archeologico Nazionale di Chiusi.

Photo: Sailko, [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Urna_cineraria_biconica_da_chiusi_IX.VII_sec._ac._01.JPG), CC BY 2.5. The file was renamed so that its name does not give the answer away.

</details>

---

## Files

| File | What it is |
|---|---|
| `prompts/` | one text file per task, ready to copy |
| `task3_finds_register_scan.jpg` | a **fake** scanned finds register, made for this course (the site "Musterdorf" does not exist) |
| `task3_finds_register_SOLUTION.csv` | the correct transcription |
| `task5_Cardarelli_2024_JCH.pdf` | the article for task 5 (open access, CC BY 4.0) |
| `task6_vase.jpg` | Villanovan urn, Chiusi. Photo by Sailko, CC BY 2.5 |
| `demo_finds_dataset.csv` | a **synthetic** finds dataset (306 finds, 4 invented sites) for the lecturer's agent demo |

## Agent demo (lecturer)

Here is the same request ([`prompts/demo_agent.txt`](prompts/demo_agent.txt)) made to a chatbot and to an agent:

```
Here is demo_finds_dataset.csv. Make three charts: (1) the number of finds per period, in chronological order; (2) the materials per site, as stacked bars; (3) a map of the finds, coloured by period. Save them as PNG and tell me what you see.
```

- The **chatbot** writes Python code: you have to run it yourself, or it describes charts it never made.
- The **agent** reads the file, writes the code, runs it, looks at the images, fixes them, and reports.
