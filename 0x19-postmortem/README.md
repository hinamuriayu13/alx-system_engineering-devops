### Postmortem: Apache 500 Internal Server Error

#### Issue Summary
- **Duration:** June 21, 2024, 14:00 UTC to June 21, 2024, 15:00 UTC
- **Impact:** The primary web service hosted on Apache was returning a 500 Internal Server Error. Users were unable to access the website, impacting 100% of the user base during the outage.
- **Root Cause:** A misnamed PHP file extension in the 'wp-settings.php' file.

#### Timeline

- **14:00 UTC:** Issue detected via monitoring alert indicating multiple 500 errors.
- **14:05 UTC:** Initial investigation began. Logs reviewed, showing PHP errors.
- **14:15 UTC:** Assumed root cause was a missing PHP module. Attempted to reinstall PHP modules.
- **14:25 UTC:** Reinstallation had no effect. Further log analysis initiated.
- **14:35 UTC:** Escalated to the learner for additional insights.
- **14:40 UTC:** Learner identified a misnamed file through `strace` output.
- **14:45 UTC:** Renamed the file from "wp-settings.phpp" to "wp-settings.php".
- **14:50 UTC:** Apache service restarted, confirming resolution.
- **15:00 UTC:** Issue fully resolved, normal service restored.

#### Root Cause and Resolution
- **Detailed Cause:** The root cause of the outage was a misnamed PHP file within the web directory. Specifically, "wp-settings.phpp" instead of "wp-settings.php". This caused Apache to fail to process the file correctly, resulting in a 500 Internal Server Error.
- **Detailed Resolution:** The issue was resolved by renaming the file from "wp-settings.phpp" to "wp-settings.php". After the file was renamed, the Apache server was restarted to apply the changes, and the service was restored.

#### Corrective and Preventative Measures
- **Improvements Needed:**
  - Implement a file extension validation check in the deployment pipeline.
  - Enhance monitoring to detect such file misconfigurations automatically.
  - Conduct regular training sessions to reduce human error in file handling.

- **Tasks to Address the Issue:**
  1. **Patch Nginx Server:** Ensure it checks file extensions before processing.
  2. **Add Monitoring on Server Memory:** Enhance monitoring to include checks for correct file extensions.
  3. **Implement Automated Script:** Create a script to validate all PHP files in the repository before deployment.
  4. **Deploy CI/CD Enhancements:** Integrate file validation checks within the CI/CD pipeline.
  5. **Conduct Training:** Organize a training session on common deployment errors and best practices for all engineers.

#### Visual Aid
![File Extension Issue Diagram](https://example.com/diagram.png)

By learning from this incident, we aim to strengthen our system’s resilience and prevent similar issues in the future. While outages are inevitable, our goal is to ensure that each one teaches us how to improve, making our system more robust and reliable.