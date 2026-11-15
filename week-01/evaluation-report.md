# Week 1: Heuristic Evaluation of the UAF Learning Management System (LMS)

**Author:** Muhammad Asim Sadiq
**Date:** 15 November 2026
**System evaluated:** UAF LMS (`lms.uaf.edu.pk`)
**Method:** Heuristic evaluation using Nielsen's 10 usability heuristics

---

## 1. Introduction: The HCI Design Life Cycle

Human-Computer Interaction (HCI) design is an iterative process, not a one-time activity. A typical life cycle has these stages:

1. **Understand users:** identify who they are and what tasks they need to do.
2. **Define requirements:** turn user needs into design goals.
3. **Design:** sketch ideas, then build wireframes and prototypes.
4. **Evaluate:** test the design with real users or experts to find usability problems.
5. **Iterate:** fix the problems and repeat the cycle.

This report covers the **evaluate** stage for an existing system. Findings from this stage feed directly into redesign.

## 2. Tool Setup

Figma was chosen as the prototyping tool because it is the industry standard for UI design and supports components, auto layout and shareable prototypes.

![Figma canvas setup](screenshots/figma-setup-1.png)
![Figma practice frame](screenshots/figma-setup-2.png)

## 3. System and Task Evaluated

**System:** the UAF LMS, used by students to access courses, attendance and results.

**Task tested:** log in as a student and check the result of one course (CS-410).

**Flow followed:**
Login → Home → Dashboard → Course page → View Result

| Step | Screenshot |
|---|---|
| Login page | `screenshots/01-login.png` |
| Home after login | `screenshots/02-home.png` |
| Dashboard | `screenshots/03-dashboard.png` |
| Course page | `screenshots/04-course-page.png` |
| Result page | `screenshots/05-result.png` |

## 4. Evaluation Method

The evaluation used **Nielsen's 10 usability heuristics**. Each problem was recorded with the screen where it occurs, the heuristic it violates, a severity rating and a suggested fix.

**Severity scale (Nielsen):**

| Rating | Meaning |
|---|---|
| 0 | Not a usability problem |
| 1 | Cosmetic problem only |
| 2 | Minor problem, low priority |
| 3 | Major problem, important to fix |
| 4 | Usability catastrophe, must fix |

Severity was judged by how often users meet the problem, how much it slows them down, and whether there is a workaround.

## 5. Findings (ordered by priority)

| # | Finding | Heuristic violated | Severity | Evidence | Suggested fix |
|---|---|---|---|---|---|
| 1 | The dashboard lists the current semester at the bottom, below older ones | Visibility of system status | 3 | `03-dashboard.png` | Sort newest first and highlight the current semester |
| 2 | Courses from different semesters sit in one flat list with no grouping | Recognition rather than recall | 3 | `03-dashboard.png` (Winter and Spring 2024-25 rows are mixed together) | Group by semester under collapsible headers, current one expanded |
| 3 | Login lands on Home (faculty categories, Vice Chancellor photo) instead of the student's Dashboard | Flexibility and efficiency of use | 2 | `02-home.png` | Redirect to the Dashboard after login |
| 4 | Home is cluttered, and "My courses" in the sidebar is truncated by "More..." | Aesthetic and minimalist design | 2 | `02-home.png` | Show the student's own courses first and move the faculty list to a separate page |
| 5 | The result page uses raw or wrong labels and has typos: "CREDIT_HR.", "Assigment", and "Department" showing "Spring 2025" | Consistency and standards; Match between system and real world | 2 | `05-result.png` | Use plain labels ("Credit Hours", "Assignment", "Semester") and fix the field mapping |
| 6 | "Fourty-eight" (a misspelling of "Forty-eight") is styled in link blue but is not clickable | Consistency and standards (false affordance) | 1 | `05-result.png` | Render it as plain text and fix the spelling |

### Detailed notes on the top findings

**Finding 1: Current semester shown last (Severity 3).**
The dashboard sorts courses oldest first, so Winter Semester 2024-25 appears above Spring Semester 2024-25. A student opening the dashboard to reach current courses must scroll past older ones. This affects every visit and has no workaround except scrolling.

**Finding 2: No semester grouping (Severity 3).**
All courses appear in one flat table. The semester is only a text value in the second column, so users must read each row to tell semesters apart. This relies on recall and scanning instead of clear visual structure.

**Finding 3: Login lands on Home, not Dashboard (Severity 2).**
After login, students see a page built around faculty categories and the Vice Chancellor's photo. Their own courses are on the Dashboard, so every login costs an extra click. It is minor per visit but it happens every time.

### Root cause for Findings 1 and 2

Both come from the same design decision: a flat, oldest-first course list. One redesign fixes both: **group by semester, newest first, current semester expanded.**

## 6. Top 3 Priorities

1. **Finding 1:** show the current semester first.
2. **Finding 2:** group courses by semester.
3. **Finding 3:** land on the Dashboard after login.

These affect every student on every visit, and all three are cheap to fix.

## 7. Conclusion

The UAF LMS works, but its main student task, reaching current courses and results, takes more steps and more scanning than necessary. The heuristic evaluation found six problems, and the most serious ones come from how the course list is ordered and grouped. A small redesign (newest-first, semester-grouped, Dashboard as the landing page) would remove the biggest pain points. In the next stage of the life cycle, these fixes would be turned into wireframes and tested with real students.

## 8. Limitations

- This was a single-evaluator heuristic evaluation. Using several evaluators would find more problems.
- No user testing was done, so the severity ratings are judgments, not measurements.
- Only one task flow was tested.
