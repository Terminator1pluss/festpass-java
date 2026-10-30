# FESTPASS
## Java Application & Jenkins CI Assignment

### Student Details
- **Student Name:** Aaryan Kalra
- **Class Code:** 001
- **GitHub Username:** Terminator1pluss
- **GitHub Repository:** https://github.com/Terminator1pluss/festpass-java

### Project Details
- **Project:** FestPass — Campus Event Registration System
- **Technology:** Java 21, Git, Jenkins
- **Jenkins Job:** festpass-ci
- **Jenkins Agent:** student-laptop
- **Git Branch:** main
- **Pipeline File:** Jenkinsfile
- **SCM Trigger:** pollSCM('* * * * *')

---

## 1. Build #1 — Initial Failure

- **Build Number:** 1
- **Commit:** c2182a8b1524264d71f9ab4ba4fadd5c54e00e7f
- **Result:** FAILURE
- **Tests:** 28
- **Passed:** 25
- **Failed:** 3
- **JAR:** Not published

### Defect Identified

The `BookingService.cancel()` method checked whether a student had booked an event but did not remove the student from the event's registration list.

As a result, cancelled seats remained occupied, and cancellation was not correctly reflected in persisted data.

### Stages Skipped
- Build JAR
- Smoke test JAR
- Save artifact

The diagnostic submission evidence CSV was still archived.

---

## 2. Defect Correction

Updated `BookingService.cancel()` to remove the student ID from the event's student collection.

The method also retains validation for bookings that do not exist.

**Fix Commit:** `5db79fd2326205e370fcb00868f971b3cfcb424d`

Existing tests and pipeline checks were not modified.

---

## 3. Build #2 — Successful Build

- **Build Number:** 2
- **Commit:** 5db79fd2326205e370fcb00868f971b3cfcb424d
- **Build Cause:** Started by an SCM change
- **Result:** SUCCESS
- **Tests:** 28
- **Failures:** 0
- **Errors:** 0
- **Skipped:** 0

The Jenkins pipeline successfully:
- Compiled the Java application.
- Executed all 28 tests.
- Built the executable JAR.
- Ran the JAR smoke test.
- Archived the build artifacts and evidence CSV.

---

## 4. JAR Verification

Command executed:

`java -jar festpass.jar help`

The executable successfully displayed the FestPass command usage:

- add-event
- list
- book
- cancel
- roster
- summary
- help

---

## 5. Submitted Evidence

The repository includes:

- Final Java source code.
- Jenkinsfile and submission configuration.
- Final executable JAR.
- Build information.
- Smoke-test output.
- Red-build evidence CSV.
- Green-build evidence CSV.

---

## 6. Conclusion

This assignment demonstrates the implementation of a Jenkins Continuous Integration pipeline using Git SCM polling, automated testing, defect diagnosis, code correction, automatic red-to-green builds, JAR generation, smoke testing, and build evidence collection.

**Submitted by: Aaryan Kalra**
