!!! info ""

    1. **Reflected XSS** - user-supplied data in HTTP request is included in webpage source without validation. It can be tested at every point of entry, including parameters in URL and URL file path.
    2. **Stored XSS** - payload is stored on the web app and then gets run when users visit the page. It can be tested at every point of entry where data can be stored, like comments on a blog, user profile information, etc.
    3. **DOM-Based XSS** - JS execution happens directly in browser without loading pages or submitting data. It happens when JS code acts as input or user interaction. Examples can be using the 'window.location.x' parameters for the attacker to gain control, or unsafe methods such as 'eval()'.
    4. **Blind XSS** - similar to stored XSS, but we cannot see the payload working. To test for blind XSS, we need to ensure the payload has a call-back (like a HTTP request) to know if code is getting executed. Tools like ```xsshunter``` can be used for blind XSS attacks.
    5. **XSS polyglot** - string of text which can escape attributes, tags and bypass filters all in one. Example - ```jaVasCript:/*-/*`/*\`/*'/*"/**/(/* */onerror=alert('THM') )//%0D%0A%0d%0a//</stYle/</titLe/</teXtarEa/</scRipt/--!>\x3csVg/<sVg/oNloAd=alert('THM')//>\x3e```

