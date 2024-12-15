# Changes Made to the Project

## 1. Added Content to Privacy Policy and Terms of Service Pages

### Privacy Policy Page
- File updated: `views/privacynotice.html`
- Added sections to explain:
  - **Introduction**  
  - **Information We Collect**  
  - **How We Use Your Information**  
  - **Data Security**  
  - **User Rights**  
  - **Contact Information**

### Terms of Service Page
- File updated: `views/terms.html`
- Added sections to outline:
  - **Acceptance of Terms**  
  - **Use of Service**  
  - **Privacy Policy Link**  
  - **User Responsibilities**  
  - **Modifications to Terms**  
- Linked the privacy policy for user reference.

---

## 2. Session Check for Access to Account Page

- Added session validation to restrict access to the **`/account`** page.  
- If the user is **not logged in**, they are redirected to the **login page**.

### Code Changes in `app.js`
```javascript
if (url.pathname === "/account" && req.method === "GET") {
    const session = getSession(req);
    if (!session) {
        return new Response(null, {
            status: 302,
            headers: { Location: "/login" },
        });
    }
    return await serveStaticFile("./views/account.html", "text/html");
}
