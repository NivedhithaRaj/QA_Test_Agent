# Login feature: requirements

## Original requirements

| ID | Requirement |
|----|-------------|
| R1 | The user should be able to log in using the login page. |
| R2 | The user should be locked out of their account after three incorrect username or password entries (failed logins). |
| R3 | The user should be logged in only after entering the correct username and password. |
| R4 | The user should see the message "Successfully logged in" once the login is successful and the home page should be visible. |

## Clarifications from the requirement owner

| ID | Question | Answer |
|----|----------|--------|
| C1 | Are the three failures consecutive or cumulative? Does a success reset the counter? | Cumulative over time. A successful login resets the counter. |
| C2 | Does the lock apply to the account or the IP/device? | IP/device. |
| C3 | What happens if the username does not exist? | Message "username does not exist, please create one" is shown instead of a lock. |
| C4 | Lock duration and message? | 30 minutes. Message "your account is locked, please try after 30 mins". |
| C5 | Is a locked user refused even with correct credentials? | Yes. |
| C6 | Failed login message? | "Failed login, username or password incorrect". |
| C7 | Are remaining attempts shown? | No. |
| C8 | Case sensitivity and length limits? | Username and password are case-sensitive. Character limit is 8. |
| C9 | Do blank submissions count as failed attempts? | Yes. |
| C10 | Success message duration and position? | 5 seconds, top right below the home icon. No redirect. |
| C11 | How is the home page identified? | Home icon. |
| C12 | Is session behavior in scope? | No. |
| C13 | Browsers in scope? | Chrome and Edge (generic). |

## Open questions

| ID | Question |
|----|----------|
| N1 | R2 and the lock message say "account", but the lock is IP/device-based. Which is intended? |
| N2 | Does a non-existent username count toward the 3 failures? (Assumed no.) |
| N3 | Do failures with different usernames from one device add up? (Assumed yes.) |
| N4 | Which message appears for both fields blank, blank username, and blank password? |
| N5 | Is the lock message shown on the 3rd failure itself? (Assumed yes.) |
| N6 | Is 8 characters a maximum for both fields? Is there a minimum? Does the field block the 9th character or does submit reject it? |
| N7 | Do attempts during a lock extend the timer? What shows for blank or non-existent usernames while locked? Does the count reset on expiry? Do old failures ever expire? |
| N8 | Are Chrome and Edge on one machine the same device? Can the lock be reset manually or a second machine used? |
| N9 | Is the login form hidden after login? Is the home icon visible on the login page before login? |
| N10 | How should the tester return to the login page after a successful login (logout is out of scope)? |
