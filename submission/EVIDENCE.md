# FestPass — Jenkins CI Assignment Evidence

## Jenkins configuration
- Job: festpass-ci
- Agent: student-laptop
- SCM branch: main
- Pipeline: Jenkinsfile
- Repository: Local Git repository
- Trigger: pollSCM('* * * * *')

## Build #1 — Failure
- Build number: 1
- Commit: c2182a8b1524264d71f9ab4ba4fadd5c54e00e7f
- Cause: Manually initiated bootstrap build
- Result: FAILURE
- Tests: 28
- Failures: 3
- JAR SHA-256: NOT_PUBLISHED

### Defect diagnosis
BookingService.cancel() checked whether a student had booked an event but did not remove the student from the event's registration list. Cancelled seats therefore remained occupied, and cancellation was not correctly reflected in persisted data.

### Stages skipped
- Build JAR
- Smoke test JAR
- Save artifact

The diagnostic evidence CSV was still archived.

## Fix
Updated BookingService.cancel() to remove the student ID from the event's student collection. The method retains validation for bookings that do not exist.

Fix commit: 5db79fd2326205e370fcb00868f971b3cfcb424d

Existing tests and pipeline checks were not modified.

## Build #2 — Success
- Build number: 2
- Commit: 5db79fd2326205e370fcb00868f971b3cfcb424d
- Cause: Started by an SCM change
- Result: SUCCESS
- Tests: 28
- Failures: 0
- Errors: 0
- Skipped: 0

The pipeline successfully built the JAR, ran the smoke test, and archived the artifacts.

## JAR verification
Executed:

    java -jar festpass.jar help

The executable displayed the FestPass command usage, including add-event, list, book, cancel, roster, summary, and help.

## Conclusion
The project demonstrates Jenkins SCM polling, automatic red/green builds, defect diagnosis and correction, automated testing, JAR creation, smoke testing, and evidence collection.
