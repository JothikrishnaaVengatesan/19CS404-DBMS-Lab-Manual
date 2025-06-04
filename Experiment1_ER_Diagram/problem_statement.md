# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

**User Requirements:**
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - JOTHIKRISHNAA V

## Scenario Chosen:
(i) University 

## ER Diagram:
(i) University
![alt text](<ER DIAGRAM 1.png>)
(ii) Hospital
![alt text](<ER DIAGRAM 2.png>)

## Entities and Attributes:
```
1. STUDENT 
Attributes:

Student_ID (Primary Key)

Name

Phone_No

Department

2. FACULTY 
Attributes:

Faculty_ID (Primary Key)

Name

Department

Student_ID (possibly foreign key showing who they supervise)

3. DEPARTMENT 
Attributes:

Department_ID (Primary Key)

Department_Name

HeadOfDepartment

Instructor

4. COURSE
Attributes:

Course_ID (Primary Key)

Student_ID (possibly foreign key)

Staff

Department

5. ASSIGNMENT
Attributes:

Assignment_ID (Primary Key)

Title

Student_ID (foreign key)

6. GRADE
Attributes:

Course_ID (Foreign Key)

Course (Reference)

Grade_Value

```

## Relationships and Constraints:
| Relationship                                   | Cardinality  | Description                                                                 |
| ---------------------------------------------- | ------------ | --------------------------------------------------------------------------- |
| `STUDENT` – MANAGES → `COURSE`                 | Many-to-Many | A student can manage many courses; a course can be managed by many students |
| `COURSE` – BELONGS TO → `DEPARTMENT`           | Many-to-One  | Many courses belong to one department                                       |
| `FACULTY` – SUPERVISES → `STUDENT`             | One-to-Many  | A faculty supervises many students                                          |
| `STUDENT MANAGEMENT` – ASSIGNS → `GRADE`       | One-to-Many  | Assigns grades per student-course                                           |
| `STUDENT MANAGEMENT` – OVERSEES → `ASSIGNMENT` | One-to-Many  | Oversees multiple assignments per student                                   |
| `STUDENT MANAGEMENT` – MANAGES → `COURSE`      | Many-to-Many | Via student management, courses are managed                                 |


## Extension (Prerequisite / Billing):
- Explain how you modeled prerequisites or billing.

Prerequisites

Modeled as: Recursive relationship on COURSE.

Why: A course can require another course as a prerequisite.

Type: Many-to-many.

Example:
Prerequisite(Course_ID, Prerequisite_Course_ID)

Billing
Modeled as: New entity linked to STUDENT.

Why: Billing has its own data (amount, due date, status).

Type: One-to-many (1 student → many bills).

Attributes: Billing_ID, Student_ID, Amount, Due_Date, Paid_Status, Payment_Date

## Design Choices:
Brief explanation of why you chose certain entities, relationships, and assumptions

Why These Entities Were Chosen:
1. STUDENT
Represents core users of the academic system.

Attributes like Student_ID, Name, and Department help track identity and affiliation.

2. FACULTY
Needed to model supervision and teaching roles.

Attributes like Faculty_ID, Department align with academic structures.

3. COURSE
Central to the system; everything revolves around course enrollment, grading, and prerequisites.

4. DEPARTMENT
Groups courses and faculty, needed for academic organization.

5. ASSIGNMENT
Represents coursework linked to students and course outcomes.

6. GRADE
Tracks student performance; must be tied to both STUDENT and COURSE.

7. BILLING (Added Entity)
Required to track student fee payments. Has multiple descriptive fields (e.g., amount, due date).

🔗 Why These Relationships Were Chosen:
1. MANAGES / ENROLLS / TAKES
Connects students to courses. Modeled as many-to-many.

2. SUPERVISES
Connects FACULTY to STUDENT. Assumes one faculty can supervise multiple students.

3. BELONGS TO
Associates COURSE with DEPARTMENT. Assumed each course belongs to one department.

4. PREREQUISITE (Recursive)
A course may depend on another course. Modeled as a many-to-many recursive relationship.

5. HAS_BILLING
Connects STUDENT to BILLING. One student can have multiple billing records.

## RESULT

Understood and applied the concepts of ER modeling by creating an ER diagram for a real-world application successfully.