```markdown id="h2k1mp"
# Log Analysis Lab

## Objective
Detect suspicious activity from server logs.

## Scenario
Multiple failed SSH login attempts from same IP.

## Findings
- Repeated failed logins indicate brute-force attempt  
- Source IP flagged for monitoring

## Mitigation
- Enable account lockout policies  
- Alert SOC for repeated attempts
