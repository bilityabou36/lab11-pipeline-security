# lab11-pipeline-security
# Lab 11 - Pipeline Security

## Objective
Build a secure CI/CD pipeline that scans application code and dependencies before deployment to reduce software supply chain risk.

## Scenario
This lab demonstrates how DevSecOps security gates can detect insecure code patterns and vulnerable dependencies early in the software development lifecycle.

## Technologies Used
- GitHub
- GitHub Actions
- Python
- Bandit
- Safety

## Zero Trust Principle
Never trust code by default. Verify continuously before deployment.

## What I Built
I created a GitHub Actions workflow that automatically runs security checks whenever code is pushed to the repository. The pipeline performs:
- static application security testing (SAST) with Bandit
- dependency vulnerability scanning with Safety

## Initial Security Findings
The first version of the application intentionally included:
- a hardcoded password in `app.py`
- an outdated dependency in `requirements.txt`

The pipeline detected the hardcoded password and failed the run, demonstrating that insecure code was blocked before release.

## Remediation Performed
I updated the application to remove the hardcoded password and replaced it with an environment variable approach:
- from: hardcoded credential
- to: `os.getenv("DB_PASSWORD")`

I also corrected the workflow configuration so the pipeline could complete successfully.

## Outcome
After remediation, the pipeline completed successfully with:
- Bandit: no issues identified
- Safety: executed successfully
- GitHub Actions workflow: passed

## Security Value
This lab shows how pipeline security supports software supply chain defense by detecting insecure code early, enforcing security checks automatically, and reducing the chance of vulnerable code reaching production.

## Evidence
See the `evidence/` folder for:
- initial insecure code
- failed pipeline run
- Bandit findings
- remediated code
- successful pipeline run
