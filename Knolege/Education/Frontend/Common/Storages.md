#frontend
**LocalStorage** 
- **Scope:** Data stored is shared across all tabs and windows for the same domain.

- **Size Limit:** Around 5-10 MB depending on the browser.

- **Persistence:** Data persists even after the browser is closed and remains until explicitly deleted by the website or the user.

- **Access:** Only accessible via JavaScript; not sent to the server with HTTP requests.

**SessionStorage**
- **Scope:** Data is stored only for the duration of the page session, i.e., until the browser (or tab) is closed.

- **Size Limit:** Similar to Local Storage, around 5-10 MB depending on the browser.

- **Persistence:** Data is deleted when the tab or browser is closed.

- **Access:** Accessible only via JavaScript; not sent with HTTP requests.

- **Use Case:** Suitable for data that should only be available during the current session (e.g., one-time form data, temporary states).

**Cookies**
- **Scope:** Data is accessible both on the client-side (via JavaScript) and sent to the server with every HTTP request.

- **Size Limit:** Typically limited to around 4 KB per cookie.

- **Persistence:** Can be set to expire at a specific time, or can last until the browser is closed if no expiration date is set.

- **Access:** Accessible by both client-side JavaScript and server-side code.

- **Use Case:** Used for storing small amounts of data, especially for tracking, authentication, or session management (e.g., login tokens).
### Key Differences:

|Aspect|**Local Storage**|**Session Storage**|**Cookies**|
|---|---|---|---|
|**Scope**|Across all windows/tabs|Per window/tab session|Domain-wide|
|**Persistence**|Until manually cleared|Until the session ends|Set by expiration or session|
|**Size Limit**|5-10 MB|5-10 MB|~4 KB per cookie|
|**Accessible By**|JavaScript|JavaScript|JavaScript + Server|
|**Data Sent to Server**|No|No|Yes (with every request)|
|**Use Case**|Long-term storage|Temporary data storage|Authentication, tracking|