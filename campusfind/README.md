# CampusFind — Java Lost & Found MVP

## Requirements
- Java 17+
- Maven 3.6+

## Run locally
1. Extract/open this folder in IntelliJ IDEA or VS Code.
2. Open a terminal in this folder.
3. Run `mvn spring-boot:run`
4. Visit `http://localhost:8080`

The UI and REST API are served together. A local H2 database file stores reports between restarts.

## Current features
- Create LOST and FOUND reports
- Search by item, category, location, description
- Filter Lost / Found
- Dashboard counts
- Change report status: OPEN, MATCHED, RETURNED
- Responsive mobile-friendly interface with a match poster beside the heading on phones
- Basic report matching by item title, description, and category
- Optional college email and optional item photo

## API
- `GET /api/reports`
- `GET /api/reports?type=LOST&q=wallet`
- `POST /api/reports`
- `PATCH /api/reports/{id}/status` with JSON such as `{"status":"RETURNED"}`

## Important
This is the first MVP, not production-ready. College mobile number is optional and not verified; there is no real login, admin permissions, or private messaging. Matching is a basic suggestion based on shared item details, not a guaranteed identification. Status controls are currently visible to all users for demonstration. Before public deployment, add authentication, role-based permissions, verified accounts, and privacy-safe contact requests.


## Frontend additions
- Responsive navigation for Home, Browse Items, My Reports, How It Works, and Help.
- Client-side search and filters for type, category, location, and date range.
- My Reports is browser-local: it lists reports submitted from this browser when the API returns the created report ID. It is not account-based.
- Possible-match suggestions use simple shared item-name/description words and category; suggestions are not proof of ownership.
- Optional mobile number is shown as a tap-to-call contact only when supplied.


## Navigation popups
- Home, Browse items, My reports, How it works and Help open dismissible popups instead of navigating immediately to page sections.
- Browse items popup allows filters to be selected; pressing Okay closes the popup and shows results in the full community board.
- My reports popup confirmation then displays locally tracked reports on the full board.


Navigation cleanup: browse filters are only in the Browse Items popup; duplicate inline controls and the full-page How It Works/Help sections have been removed because those guides are available as popups. Report cards remain on the main page.


Latest update: the quick-search field is visible below the header on Home, while the Browse reports heading is reserved for the Browse items flow. The frontend no longer imposes a 2 MB photo cap; practical upload size is still limited by available memory, database/storage capacity, and browser/device performance.


### Returned-items poster
The hero poster now displays only reports whose status is `RETURNED`. It shows the most recently created returned report. If no reports have been marked returned, it displays “No items returned yet”. A report must be explicitly marked Returned from its report card; LOST/FOUND status alone does not qualify.
