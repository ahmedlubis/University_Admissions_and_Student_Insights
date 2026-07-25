# 🎓 Academic Information System Dataset

## 📖 Dataset Overview

This dataset represents several core business processes within a university academic information system, covering the complete student lifecycle—from admission, academic activities, graduation, to study program master data.

The database consists of **four interconnected datasets** that can be linked using student identifiers such as the **Student Identification Number (NIM)** and study program information.

---

# 🗂️ Dataset Description

## 1. Admission Data (`admisi.csv`)

This table records the **student admission process** at the university.

It contains applicant registration information along with attributes that indicate each applicant's final admission status.

Applicants who successfully pass the admission process and officially enroll as students are assigned a **Student Identification Number (NIM)**.

### Key Characteristics

- Records applicant registration data
- Indicates admission status
- Generates a **NIM** for accepted applicants
- The **NIM** is designed as a **Smart Key**, uniquely identifying each student throughout their academic lifecycle

---

## 2. Academic Activity Data (`aktivitas-perkuliahan.csv`)

This table records students' academic activities throughout their studies.

It includes course enrollments, semester records, remedial programs, credit loads (SKS), and letter grades obtained in each course.

The recorded grades are later converted into numerical grade points and used to calculate each student's **Grade Point Average (GPA / IPK)**.

---

### GPA (IPK) Calculation

The cumulative GPA is calculated using the standard weighted-average formula:

```text
GPA (IPK) = Σ(Grade Point × Credit Hours) / Σ(Credit Hours)
```

where:

- **Grade Point** = Numerical value assigned to each letter grade
- **Credit Hours (SKS)** = Credit weight of each course

---

### Semester Code Format

Semester codes follow the format:

```text
[Academic Year (4 digits)][Semester Code (1 digit)]
```

Example:

```text
20251
```

represents:

- **Academic Year:** 2025/2026
- **Semester:** Odd Semester

---

### Semester Code Classification

| Code | Semester Type |
|------|---------------|
| **1** | Odd Semester |
| **2** | Even Semester |
| **3** | Odd Semester Remedial |
| **4** | Even Semester Remedial |

---

### Letter Grade Conversion

| Grade | Grade Point |
|-------|------------:|
| **A** | 4.00 |
| **A-** | 3.70 |
| **B+** | 3.30 |
| **B** | 3.00 |
| **B-** | 2.70 |
| **C+** | 2.30 |
| **C** | 2.00 |
| **D** | 1.00 |
| **E** | 0.00 |

---

## 3. Graduation Data (`peserta-wisuda-tervalidasi.csv`)

This table records students who have successfully completed all academic requirements and have been officially validated as graduation ceremony participants.

### Key Characteristics

- Records graduation eligibility
- Indicates students who have fulfilled all academic requirements
- Contains validated graduation participant information
- Represents the final stage of the student academic lifecycle

---

## 4. Study Program Master Data (`homebase.csv`)

This table serves as the **master reference dataset** for institutional academic classifications.

It provides standardized information regarding:

- Faculty
- Degree level
- Study program

The dataset is primarily used as a reference table for integrating and categorizing academic records across the other datasets.

### Key Characteristics

- Faculty information
- Degree level classification
- Study program information
- Reference (master) data for academic reporting

---

# 📌 Dataset Relationships

The four datasets collectively describe the complete academic journey of a university student:

```text
Admission
     │
     ▼
Student (NIM)
     │
     ▼
Academic Activities
     │
     ▼
Graduation
```

The **Study Program Master Data (`homebase.csv`)** acts as a reference table that supports and enriches information across all academic datasets.

---

# 📝 Summary

This dataset provides a comprehensive representation of university academic operations, covering:

- Student admission processes
- Academic activities and course performance
- GPA (IPK) calculation
- Semester classifications
- Graduation records
- Faculty and study program master data

Because these datasets represent sequential academic business processes, they are well suited for applications such as:

- Academic performance analysis
- Student progression tracking
- Graduation analytics
- Institutional reporting
- Educational data mining
- Student success prediction
- Academic dashboard development
