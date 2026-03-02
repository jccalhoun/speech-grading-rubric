# 🎤 Informative Speech Grading Tool

An offline-capable, browser-based grading rubric for evaluating informative speeches. Built for classroom use at Ivy Tech Community College as a replacement for Google Forms — works without an internet connection and exports results in the same format as Google Forms responses.

> **Note:** This project was created with AI assistance using [Claude](https://claude.ai) by Anthropic. The rubric content, grading criteria, and workflow requirements were provided by the instructor; the application was iteratively designed and built through a collaborative conversation.

---

## ✨ Features

- **Full rubric grading** — 17 rubric items across Introduction, Delivery, Content, Visual Aids, and Conclusion
- **Quick-select comment chips** — pre-loaded feedback phrases for each item, plus a free-text field for custom comments
- **Session management** — grade multiple students in one sitting; all grades are held in a session until you export
- **Export to CSV** — one row per student, matching the column structure of Google Forms responses, with Total and Percentage columns appended
- **Persistent storage** — session and roster are auto-saved to `localStorage`; a restore prompt appears if you reopen the file mid-session
- **Editable roster** — add, edit, or remove student names; paste a whole class list at once (one name per line)
- **Um/uh counter** — floating button to tally filler words during the speech; count is saved with the grade and exported to CSV
- **Validation** — prevents saving until every rubric item has both a score and at least one comment; scrolls to and highlights incomplete items
- **Live score display** — running total and percentage in the header updates as you grade
- **Fully offline** — single `.html` file with no dependencies beyond optional Google Fonts

---

## 🚀 Getting Started

No installation required.

1. Download `speech_grader.html`
2. Open it in any modern browser (Chrome, Firefox, Safari, Edge)
3. Click **✎ Roster** to add your students
4. Select a student, fill out the rubric, and click **＋ Save Grade to Session**
5. Repeat for each student
6. Click **⬇ Export All** to download a single CSV with all grades

---

## 📋 Rubric Structure

| Section | Items | Max Points |
|---|---|---|
| Introduction | Attention getter, Topic clarity, Credibility, Preview | 17 |
| Delivery | Notes, Eye contact, Movement, Volume/pace/tone, Extemporaneous | 25 |
| Content | Informative, Audience relation, Main points, Verbal sources, Source quality | 29 |
| Visual Aids | Design and presence | 4 |
| Conclusion | Transitions, Summary, Closer | 15 |
| **Total** | | **90** |

---

## 📤 CSV Export Format

The exported CSV matches the Google Forms response format exactly, making it compatible with existing gradebooks. Each row represents one student with the following columns:

- `Timestamp` — when the grade was saved
- `Speaker's name`
- One column per rubric item (score), followed by one column for its comments
- `time` — speech duration
- `Comments` — overall feedback
- `Um Count` — total um/uh tally
- `Total` — raw point total
- `Percentage` — score as a percentage to two decimal places

---

## 💾 Data Persistence

All data is stored in the browser's `localStorage` under two keys:

| Key | Contents |
|---|---|
| `speechGrader_session` | All saved grades for the current session |
| `speechGrader_roster` | Student names |

Because data lives in `localStorage`, it is:
- **Tied to the browser and device** — data won't transfer if you switch browsers or computers
- **Persistent across tab closes** — a restore prompt appears on reopen if unsaved grades exist
- **Not synced** — for shared use across devices, export the CSV before closing

---

## 🛠️ Customization

The rubric, comments, and point values are defined in the `RUBRIC` array near the top of the `<script>` block. Each item follows this structure:

```javascript
{
  id: "unique_id",
  label: "Rubric item label",
  max: 5,                        // maximum points
  comments: ["Good", "Feedback option 2", "Feedback option 3"]
}
```

The first comment in each array appears as the first chip — by convention this is `"Good"` so positive feedback is always one tap away.

---

## 🌐 Browser Compatibility

| Browser | Status |
|---|---|
| Chrome / Edge | ✅ Fully supported |
| Firefox | ✅ Fully supported |
| Safari | ✅ Fully supported |
| Mobile browsers | ✅ Responsive layout |

---

## 📁 File Structure

This is a single-file application — all HTML, CSS, and JavaScript are contained in `speech_grader.html`. There are no build steps, dependencies, or server requirements.

---

## 🤖 AI Assistance

This tool was built through an iterative conversation with **Claude Sonnet** (Anthropic). The development process involved:

- Describing the existing Google Forms workflow and desired offline replacement
- Uploading the original rubric HTML and a sample export spreadsheet to match the output format
- Iteratively adding features (session management, localStorage persistence, roster editor, um counter, validation) across multiple rounds of feedback
- Bug fixes and refinements based on real-world testing in Firefox and Chrome

The rubric content, grading philosophy, and pedagogical decisions are entirely the instructor's own. Claude handled the implementation.

---

## 📄 License

This project is intended for personal classroom use. Feel free to adapt it for your own grading needs.
