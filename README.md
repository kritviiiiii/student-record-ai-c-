# AI-Assisted Student Record and Result Management System

**Course Code**: PRC1001  
**Course Name**: Programming in C  
**Academic Program**: B.Tech Computer Science and Engineering (Semester I)  
**Institution**: University of Petroleum and Energy Studies (UPES), Dehradun  
**Student Name**: Kritvi  
**SAP ID**: 590035544  
**Roll No.**: R214226025  
**Repository**: [kritviiiiii/student-record-ai-c-](https://github.com/kritviiiiii/student-record-ai-c-)  

---

## 📖 Table of Contents
1. [Project Overview](#-project-overview)
2. [Key Features](#-key-features)
   - [Part A: Core C Requirements](#part-a--core-c-requirements)
   - [Part B: AI-Assisted Academic Advisor](#part-b--ai-assisted-academic-advisor)
3. [Data Structures & Design](#-data-structures--design)
4. [Compilation & Execution Instructions](#-compilation--execution-instructions)
5. [Menu Navigation & Usage Guide](#-menu-navigation--usage-guide)
6. [Academic Advisor Logic & Decision Matrix](#-academic-advisor-logic--decision-matrix)
7. [Testing & Verification](#-testing--verification)
8. [GitHub Workflow & Commit History](#-github-workflow--commit-history)
9. [Viva Preparation & Concept Summary](#-viva-preparation--concept-summary)

---

## 📌 Project Overview
The **AI-Assisted Student Record and Result Management System** is a robust console-based, menu-driven software application written in standard C. Developed as a semester project for **PRC1001 (Programming in C)**, it bridges fundamental C constructs—structures, arrays, loops, string operations, sorting algorithms, and modular functions—with modern software development practices including Git version control, GitHub issue tracking, and an AI-assisted heuristic Academic Advisor module.

---

## 🎯 Key Features

### Part A – Core C Requirements
1. **Menu-Driven Interface**: Clean, looped console UI providing seamless user access to 9 distinct functional options and a safe exit.
2. **Preloaded Baseline Records**: Program initializes with 5 verified student profiles covering all 4 academic years (1st, 2nd, 3rd, and 4th years).
3. **Record Storage**: Comprehensive data tracking for each student:
   - `SAP ID` (Unique 9-digit `long int`)
   - `Roll No.` (String alphanumeric identifier)
   - `Name` (Full name string, supporting whitespace)
   - `Phone No.` (Contact string)
   - `Email ID` (Official university email string)
   - `Year` (Integer 1 to 4)
   - `Semester` (Integer 1 to 8)
   - `SGPA Array` (`float[8]` storing Semester Grade Point Averages; `0.0` for upcoming semesters)
   - `CGPA` (Calculated cumulative grade point average)
4. **Student Record Operations**:
   - **Add Student**: Interactive data entry with automated duplication checks against existing SAP IDs and input bounding.
   - **Search Record**: Fast linear search by SAP ID displaying complete student profile and semester breakdown.
   - **Delete Record**: Deletes an existing record by SAP ID and shifts subsequent array elements leftward to maintain continuous memory.
   - **Display All Records**: Formatted, card-style breakdown of all enrolled student records.
5. **Analytics & Sorting**:
   - **CGPA Calculation**: Computes dynamic average based solely on completed semesters (`sgpa > 0.0`), preventing artificial score deflation for junior students.
   - **Cohort Analysis (Year-wise Average CGPA)**: Aggregates performance by academic year (1st through 4th) to analyze batch trends.
   - **Sort by SAP ID**: Bubble sort arranging records in ascending order of SAP ID on a copied array (preserving primary entry order).
   - **Sort by Name**: Alphabetical ascending bubble sort using `strcmp()` on a copied array.

### Part B – AI-Assisted Academic Advisor
- Employs a heuristic decision-making engine in C suggested and refined using AI tools.
- Evaluates student CGPA against 4 defined performance tiers.
- Performs diagnostic analysis by looping across semester SGPAs to identify the specific lowest-scoring semester and generate actionable counsel.
- Offers dual execution: single student lookup or comprehensive whole-class advisory report.

---

## 🏗 Data Structures & Design

```c
#define MAX_STUDENTS 100
#define TOTAL_SEMESTERS 8

struct Student {
    long int sap_id;             /* Unique student identifier */
    char roll_no[20];            /* Alphanumeric roll number */
    char name[50];               /* Full student name */
    char phone[15];              /* Contact phone number */
    char email[50];              /* Email address */
    int year;                    /* Current academic year (1-4) */
    int semester;                /* Current semester (1-8) */
    float sgpa[TOTAL_SEMESTERS]; /* SGPA history for up to 8 terms */
    float cgpa;                  /* Cumulative Grade Point Average */
};

/* Database array */
struct Student students[MAX_STUDENTS];
int student_count = 0;
```

---

## ⚙️ Compilation & Execution Instructions

### Prerequisites
- GCC Compiler (MinGW / TDM-GCC / GCC on Linux / Clang on macOS)

### 1. Compile the Program
Open a terminal in the project directory:
```bash
gcc -Wall -Wextra 590035544.c -o 590035544.exe
```

### 2. Run Interactively
```bash
.\590035544.exe
```

### 3. Run Automated Test Suite
```bash
.\590035544.exe < tests\sample_input.txt > tests\sample_output.txt
```

---

## 🧭 Menu Navigation & Usage Guide

```text
------------------------- MAIN MENU -------------------------
1. Add Student Details
2. Search and Display a Student Record
3. Calculate CGPA of Each Student
4. Calculate Average CGPA of Students by Year
5. Display Records of All Students
6. Delete an Individual Student Record
7. Display All Records in Increasing Order of SAP ID
8. Display All Records in Increasing Order of Name
9. AI-Assisted Academic Advisor
0. Exit
-------------------------------------------------------------
```

---

## 🤖 Academic Advisor Logic & Decision Matrix

The academic advice module evaluates the student's dynamic CGPA and pinpoints their lowest completed semester:

| Performance Tier | CGPA Range | Recommendation Message |
| :--- | :--- | :--- |
| **Excellent Performance** | $\text{CGPA} \ge 8.5$ | Excellent performance – maintain your current study pattern and explore competitive coding, internships, or mini-projects. |
| **Good Performance** | $7.0 \le \text{CGPA} < 8.5$ | Good performance – stay consistent with lecture notes and revise core subjects to push your CGPA above 8.5. |
| **Needs Improvement** | $5.5 \le \text{CGPA} < 7.0$ | Needs improvement – focus more on subjects with lower SGPA and solve extra practice problems before mid-sem/end-sem exams. |
| **Requires Immediate Attention** | $\text{CGPA} < 5.5$ | Requires immediate attention – meet your faculty advisor, attend remedial doubt sessions, and clear core fundamentals. |

---

## 🧪 Testing & Verification

The program includes sample input and verified output files under the `tests/` directory:
- `tests/sample_input.txt`: Scripted inputs covering display, CGPA calculation, year-wise analytics, sorting by SAP ID and Name, searching, advisory reports, adding a record, and deleting a record.
- `tests/sample_output.txt`: Complete execution log proving correctness across all 4 tiers and boundary conditions.

---

## 📦 GitHub Workflow & Commit History

This repository demonstrates structured Git version control adhering to course guidelines:

1. **Commit 1**: `Initial C program: define student structure and project skeleton`
2. **Commit 2**: `Implement student record functions: add, search, delete, and display records`
3. **Commit 3**: `Implement CGPA calculation and sorting algorithms by SAP ID and Name (Closes #1)`
4. **Commit 4**: `AI-assisted advisor + documentation: heuristic advisor engine, test suite, and AI usage log`

---

## 🎓 Viva Preparation & Concept Summary

1. **How is CGPA computed without deflating junior students' scores?**
   - The loop checks `sgpa[i] > 0.0f` and increments `completed_sems`. The sum is divided by `completed_sems` rather than a static 8.
2. **How do sorting functions keep the database array unmodified?**
   - Records are copied into a local `struct Student temp_list[MAX_STUDENTS]` array prior to running Bubble Sort.
3. **How does deletion maintain array continuity?**
   - After locating the target index, subsequent elements are shifted left (`students[j] = students[j+1]`) and `student_count` is decremented.
4. **How was AI utilized in the project?**
   - AI served as a conceptual assistant to formulate the advisory rubric, validate edge cases, and design test suites (documented in `AI_USAGE_LOG.md`).
