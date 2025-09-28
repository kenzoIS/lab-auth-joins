Lab 3 – Joins and API Reports
### SQL Joins Explained

A) INNER JOIN — Users who have at least one role
Returns only users that have a matching role in user_roles. Users without roles are excluded.

B) LEFT JOIN — All users (with profile info if present)
Returns all users regardless of whether they have a profile. If a user doesn’t have a profile, profile fields are NULL.

C) RIGHT JOIN — Keep all roles even if unassigned
Returns all roles, even those not assigned to any user. Users without that role show as NULL.

D) FULL OUTER JOIN (emulated) — Profiles vs Users
Emulates a full outer join by combining LEFT JOIN and RIGHT JOIN. Shows all users and profiles, even if one side is missing.

E) CROSS JOIN — Every user × every role
Generates all possible combinations of users and roles. Each user is paired with every role.

F) SELF JOIN — Who referred whom
Joins the referrals table to users twice: once to get the referrer’s info, and once for the referred user. Shows who referred whom along with referral dates.

G) Bonus — Latest login per user (LEFT JOIN + subquery)
Uses a subquery to get each user’s most recent login and left joins it to all users. Users without logins still appear with NULL for login info.

### API Reports Endpoints
Endpoint	Purpose
GET /api/reports/users-with-roles	- Retrieves all users that have at least one role assigned.
GET /api/reports/users-with-profiles - Lists all users with their profile information, if present.
GET /api/reports/roles-right-join	- Shows all roles, including those not assigned to any user.
GET /api/reports/profiles-full-outer	- Returns a full outer join view of users and profiles, showing all entries.
GET /api/reports/user-role-combos	- Displays every possible combination of user × role.
GET /api/reports/referrals	- Shows referral relationships: who referred whom and when.
GET /api/reports/latest-login	- Shows each user’s latest login info; users without logins are included with NULL.


### All endpoints require a valid JWT token. Include it in the header as:
Authorization: Bearer <your_token>