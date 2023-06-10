#hacking #attacks

# Clickjacking

Clickjacking, also known as "UI redress attack", is a malicious technique used by attackers to trick a user into clicking on something different from what the user perceives, potentially causing them to reveal confidential information or take control of their computer while clicking on seemingly innocuous web pages.

Clickjacking works by overlaying an invisible frame (like an iframe or a transparent layer) over a webpage. The overlaid frame contains malicious content, but the user sees the legitimate webpage beneath it. When the user interacts with the webpage (for example, clicking on a button), they're actually interacting with the invisible, malicious content.

One common clickjacking scam involves tricking users into clicking a button that shares a website on their social media profile without their knowledge or consent. Other clickjacking attacks might try to trick users into revealing sensitive information like passwords and credit card numbers.

Clickjacking can be mitigated through various techniques, such as implementing X-Frame-Options (XFO) HTTP response headers, Content Security Policy (CSP), and Framebusting/Framekiller scripts. Additionally, always being cautious while interacting with web content and keeping web browsers updated can help avoid such attacks.

Certainly, here's a more comprehensive explanation incorporating all your points:

1. **Clickjacking, also known as User-Interface Redressing**: This is a vulnerability that can trick users into clicking a malicious button that has been cleverly disguised to look like a legitimate element. It's a deceptive method where hackers manipulate the interface to mislead users into performing unintended actions.

2. **How Hackers Achieve Clickjacking**: Hackers accomplish clickjacking by using HTML page overlay techniques to hide one web page within another. This means they layer a deceptive, invisible page over a legitimate one, deceiving the user into interacting with the hidden page while believing they are interacting with the genuine one.

3. **Reliance on the HTML feature iFrame**: The core of this technique lies in a feature of HTML called iFrame (Inline Frame). iFrames allow developers to embed one web page within another, and it's this feature that's exploited in clickjacking attacks. The malicious web page is embedded invisibly over the legitimate page, and user interactions with the perceived page are actually interactions with the hidden, malicious page.

4. **Hunting for Clickjacking**: If you're looking to detect potential clickjacking, you should:
    - Look for state-changing actions, such as buttons or links that modify data or change settings. These are prime targets for clickjacking attacks.
    - Check the response headers of the webpage. Headers like X-Frame-Options and Content-Security-Policy can help identify pages that are protected against clickjacking.

5. **Prevention of Clickjacking**: Here are some measures to prevent clickjacking:
    - Implement the Content-Security-Policy (CSP) response header. This header allows you to control which sites can embed your page, which can prevent your page from being embedded in a malicious site.
    - Set the 'frame-ancestors' directive to a specific origin in your CSP. This will allow only that specific origin to frame your content, adding an additional layer of security.
    - Implement SameSite cookies. These cookies enhance security by preventing the browser from sending the cookie along with cross-site requests, which can help protect against cross-site request forgery attacks, including clickjacking.