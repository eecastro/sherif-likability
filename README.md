# Perceived Likability

A two-task partner activity, loosely based on the Robbers Cave experiment. Partners first compete at Tic-Tac-Toe, then cooperate on building a twelve-cup red Solo cup tower. After each task, each partner privately rates how they feel about the other on a 1–5 scale. The teacher dashboard shows how each student's rating changed from the competition task to the cooperation task.

Converted from the Google Form "Perceived likability."

## Files

| File | Purpose |
|---|---|
| `index.html` | Student page |
| `config.js` | The one place to paste the Apps Script URL and an optional session code |
| `Code.gs` | Apps Script backend that writes to a Google Sheet |
| `dashboard.html` | Teacher dashboard (teacher key required) |

## One-time setup

1. **Create the Sheet.** Make a new Google Sheet, for example "Perceived Likability Responses."
2. **Add the script.** In the Sheet, go to Extensions > Apps Script. Replace the default code with `Code.gs`, then save.
3. **Create the tab.** Choose `setup` in the function dropdown and click Run. Authorize when asked. This creates a "Responses" tab with headers.
4. **Set the teacher key.** In Apps Script, go to Project Settings (gear) > Script properties > Add script property. Name it `TEACHER_KEY`. Use a long random string that only you know. Do not put this key in the repository.
5. **Deploy.** Click Deploy > New deployment > type "Web app."
   - Execute as: **Me**
   - Who has access: **Anyone**

   "Anyone within your school" makes students sign in, which blocks the page.
6. **Connect the page.** Copy the Web app URL (it ends in `/exec`) into `config.js` as `apiUrl`.
7. **Publish on GitHub.** Create a public repository named `sherif-likability` under `eecastro`. Upload all files, then go to Settings > Pages and deploy from the `main` branch, root folder.

Your links will be:

- Students: `https://eecastro.github.io/sherif-likability/?session=F26-SocialPsych-1`
- Teacher dashboard: `https://eecastro.github.io/sherif-likability/dashboard.html`

## Running the activity

- **Session codes.** Make one code for each run of the activity, such as `F26-SocialPsych-1` or `S27-SocialPsych-2`. Group numbers repeat across runs, so the session code keeps each run's groups separate. Put the code in the student link or in `config.js`.
- **Group and seat.** Students enter their group number (the number you counted off) and whether they are Partner 1 or Partner 2. Their names are not collected. To match rows to students, use your roster, which maps each group and seat to names.
- **Order.** Students answer once after the Tic-Tac-Toe game and once after the Tower task. Each answer is one row.
- **Corrections.** If a student submits again for the same session, group, seat and task, the earlier answer is replaced.

## What the dashboard shows

- **Change** is the cooperation rating minus the competition rating for each rater. It is positive when the student liked their partner more after cooperating.
- Only ratings where both tasks are complete count toward the summary. Rows still waiting on the second task are counted separately.
- The Session filter defaults to all sessions combined, so you can aggregate across semesters. Choose one session to look at a single run.
- Download CSV exports the table for the current filter.

## Privacy

- No names, emails or class periods are collected.
- Students never see results, and their partner cannot see their answers.
- Anyone with the student link can submit a response. Only someone with the teacher key can read the data.
- The teacher key is entered on the dashboard and is not stored by the page. If you bookmark the dashboard with `?tk=` in the URL, that key is saved in your browser history, so do not share that link.

## Updating after a change to Code.gs

Deploy > Manage deployments > edit the deployment > Version: New version > Deploy. The URL stays the same, so `config.js` does not need to change. Re-run `setup` only if you change the headers.

## Notes

- Results are for classroom discussion, not for scoring students.
- Group size is assumed to be two. The dashboard reads Partner 1 and Partner 2 within each group.
