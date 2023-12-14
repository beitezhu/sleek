---
layout: post
title: Getting Started with Sleek
featured-img: sleek
mathjax: true
---

# Getting started

[GitHub Pages](https://pages.github.com) can automatically generate and serve the website for you.
Let's say you have a username/organisation `my-org` and project `my-proj`; if you locate Jekyll source under `blog` folder of master branch in your repo `github.com/my-org/my-proj`, the website will be served on `my-org.github.io/my-proj`.

1. Just download or fork and clone the source from [github.com/janczizikow/sleek](https://github.com/janczizikow/sleek/).
2. Make sure your local machine has ruby and node
3. Edit site settings in  `_config.yml` file according to your project.
4. Replace `favicons` and `_includes/logo.svg` with your own logo.

**Note** that you might have to adjust some CSS depending on the width and height of your logo. You can find Header / Navigation related SCSS in `_sass/layout/nav.scss`.

## Writing content

### Posts

Create a new Markdown file such as `2017-01-13-my-post.md` in `_post` folder. Configure YAML Front Matter (stuff between `---`):

```yaml

---
layout: post # needs to be post
title: Getting Started with Sleek # title of your post
featured-img: sleek #optional - if you want you can include hero image
---

```

#### Images

In case you want to add a hero image to the post, apart from changing `featured-img` in YAML, you also need to add the image file to the project. To do so, just upload an image in `.jpg` format to `_img` folder. The name must before the `.jpg` file extension has to match with `featured-img` in YAML. Next, run `gulp img` from command line to generate optimized version of the image and all the thumbnails. You have to restart  the jekyll server to see the changes. Sleek uses [Lazy Sizes](https://github.com/aFarkas/lazysizes) Lazy Loader for loading images. Check the link for more info. Lazy Sizes doesnt't require any configuration and it's going to be included in your bundled js file.

### Pages

The home page is located under `index.md` file. To change the content or design you have to edit the `default.html` file in `_layouts` folder.

In order to add a new page, create a new html or markdown file under root directory or inside `_pages` folder. To add a link to the page, edit `navigation` setting in `_config.yml`.

### Images TODO

Introduce gulp optimization

Breakpoint | Image Type | Width | Retina
------------ | ------------ | ------------- | -------------
xs |Post Thumb | 535px | 1070px
sm |Post Thumb | 500px| 1000px
md |Post Thumb | 329.375px | 658.75px
lg |Post Thumb | 445.625px | 891.25px
xl |Post Thumb | 353.125px | 706.25px

Breakpoint | Image Type | Width | Retina
------------ | ------------ | ------------- | -------------
xs |Post Hero | 535px | 1070px
sm |Post Hero | 500px| 1000px
md |Post Hero | 329.375px | 658.75px
lg |Post Hero | 445.625px | 891.25px
xl |Post Hero | 353.125px | 706.25px

### MathJax

If you want to use [MathJax](https://www.mathjax.org/) in your posts, add `mathjax: true` in [YAML front matter](https://jekyllrb.com/docs/frontmatter/) of your post:

```yaml
---
layout: post
title: Blog Post with MathJax
featured-img: sleek # optional - if you want you can include name of hero image
mathjax: true # add this line in order to enable MathJax in the post
---
```

#### Example

In N-dimensional simplex noise, the squared kernel summation radius $r^2$ is $\frac 1 2$
for all values of N. This is because the edge length of the N-simplex $s = \sqrt {\frac {N} {N + 1}}$
divides out of the N-simplex height $h = s \sqrt {\frac {N + 1} {2N}}$.
The kerel summation radius $r$ is equal to the N-simplex height $h$.

$$ r = h = \sqrt{\frac {1} {2}} = \sqrt{\frac {N} {N+1}} \sqrt{\frac {N+1} {2N}} $$
Happy hacking!


    
## **1. Purpose and Overview**

### **Overview:**

Synology Account, a critical SaaS service with over 5 million users, serves as the gateway to all Synology cloud services, including QuickConnect, Active Insight, and C2. The security of Synology Account is paramount, impacting both users and the company. It also facilitates user engagement in Synology Events and community participation.



### **Objective:**

To enhance the security of our cloud service, particularly as the integration of products with the Synology Account escalates.

### **Approach:**

- Introduce diverse methods for straightforward multi-factor authentication (MFA) setup.
- Foster user engagement in enabling two-factor authentication (2FA) through education on its significance.
- Strengthen account security, independent of 2FA activation.

## **2. Current State Analysis**

- In 2020, a brute force attack caused data loss and incurred about $100,000 in damages, affecting around 50 NAS users. Although the impact was limited to less than 0.1% of users, it underscored the need for enhanced product security.
- Currently, the adoption rate of 2FA is only 1%, with OTP as the sole available option.
- Certain legacy portals are restricted to OTP for 2FA, pending upgrades by users.

## **3. Problem Statement**

- **Low Adoption Rate of Two-Factor Authentication (2FA)**: Currently, only a minimal 1% of users have enabled 2FA, predominantly due to the perceived complexity and inconvenience associated with traditional 2FA methods like One-Time Passwords (OTP).
- **User Inaccessibility and Convenience Issues**: Many users face challenges in accessing or managing their 2FA settings, especially in scenarios such as phone loss or OTP inaccessibility. This leads to a reliance on technical support and a general reluctance to engage with existing security measures.
- **Limited Variety in Security Options**: The current security framework primarily relies on OTPs, lacking diversity in authentication methods. This limitation fails to address the varying needs and preferences of a diverse user base.
- **Need for Enhanced User Awareness and Engagement**: There is a significant gap in user understanding and involvement regarding their account's security settings. Users often do not regularly check or update their security preferences, partly due to the lack of a user-friendly interface.

**Out of Scope**

- Mandatory 2FA implementation remains outside our current scope, focusing instead on voluntary adoption supported by user education and enhanced security features.

## **4. Research Methodology**

### **Survey and Inquiry:**

- Collected 500 responses identifying the top three reasons for low MFA setup: perceived cumbersomeness, uncertainty about setup, and fear of being locked out post-setup.

### **User Interviews:**

- Discovered issues with double password entry inconvenience and fears of losing access due to accidental app deletion.

### **Competitive Analysis:**

- Examined Google, Microsoft, and Adobe’s security login methods. Noted each offers more than two 2FA methods, including OTP and phone push notifications.


| Feature                          | Google                                   | Microsoft                                       | Adobe                      |
|----------------------------------|------------------------------------------|-------------------------------------------------|----------------------------|
| Two-Factor Authentication (2FA)  | Yes                                      | Yes                                             | Yes                        |
| Authentication Methods           | OTP, Push Notification, U2F Key          | OTP, Push Notification, Physical Security Key   | OTP, SMS, Email            |
| Backup Methods                   | Backup Codes, Secondary Email            | Secondary Email, Security Questions             | Recovery Email             |
| User Interface                   | User-friendly, Intuitive                 | Intuitive, Comprehensive                        | Simple, Straightforward    |
| Recovery Options                 | Email, Phone                             | Email, Phone, Security Questions                | Email                      |
| Additional Security Features     | Advanced Protection Program              | Microsoft Authenticator App                     | Adobe Account Access       |






![]({{ site.baseurl }}/images/SA-research.jpeg)



## **6. Proposed solution**

 <table>
        <tr>
            <th>Proposed Solution</th>
            <th>Pros</th>
            <th>Cons</th>
        </tr>
        <tr>
            <td>New Login Method: "Approve Signin" Feature</td>
            <td>
                <ul>
                    <li>Enhances security against phishing by diminishing password reliance</li>
                    <li>Convenient for users: simple approval via phone</li>
                    <li>Accessible for those who find traditional 2FA methods cumbersome</li>
                </ul>
            </td>
            <td>
                <ul>
                    <li>Requires stable internet connectivity</li>
                    <li>Necessitates downloading an additional Synology Secure Signin app</li>
                    <li>Learning curve: relatively new approach in the market</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Overview Page: Simplified Interface for Security Settings</td>
            <td>
                <ul>
                    <li>User-friendly interface improves understanding of security settings</li>
                    <li>Promotes user engagement in security practices</li>
                    <li>Highlights the importance of security to users</li>
                </ul>
            </td>
            <td>
                <ul>
                    <li>Development demands time and resources</li>
                    <li>Needs regular updates for new features and threats</li>
                    <li>Users less likely to check settings regularly as it requires web service login</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Abnormal Sign-in Notification: Login Attempt Alerts</td>
            <td>
                <ul>
                    <li>Increases awareness of unauthorized access attempts</li>
                    <li>Enables prompt response to potential breaches if they didn't log in</li>
                </ul>
            </td>
            <td>
                <ul>
                    <li>Risk of notification fatigue in users</li>
                    <li>Potential for false alarms leading to undue concern</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Abnormal Sign-in Compulsory 2FA: Mandatory 2FA for Abnormal IPs</td>
            <td>
                <ul>
                    <li>Enhances security level by enforcing 2FA on suspicious login attempts</li>
                </ul>
            </td>
            <td>
                <ul>
                    <li>Can be cumbersome for users, especially if falsely identified as abnormal</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Security Key Integration</td>
            <td>
                <ul>
                    <li>Provides a highly secure, physical authentication method</li>
                    <li>Useful for users without smartphone access</li>
                    <li>Adds a new security option for users</li>
                </ul>
            </td>
            <td>
                <ul>
                    <li>Incurs additional costs for users to acquire keys</li>
                    <li>Not essential for all, potentially confusing as an unfamiliar option</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Legacy Portal: Update with Advanced 2FA Options</td>
            <td>
                <ul>
                    <li>Upgrades outdated systems to current standards</li>
                    <li>Extends protection to more users</li>
                </ul>
            </td>
            <td>
                <ul>
                    <li>Significant development and testing required</li>
                    <li>Challenges with compatibility in legacy systems</li>
               </ul>
            </td>

 
 


<!-- 加入空行 -->
![]({{ site.baseurl }}/images/SA-overview.jpeg)


## **7. Product MVP Requirements**


   <table>
        <tr>
            <th>#</th>
            <th>Component</th>
            <th>Feature</th>
            <th>Priority</th>
        </tr>
        <tr>
            <td>1</td>
            <td>Visual Appearance</td>
            <td>Design of Overview Page to Identify Account Security Level</td>
            <td>P1</td>
        </tr>
        <tr>
            <td>2</td>
            <td>Backend</td>
            <td>Backend Development for "Approve Signin" Service</td>
            <td>P1</td>
        </tr>
        <tr>
            <td>3</td>
            <td>Mobile App Development</td>
            <td>Mobile App for Push Notification (Approve Signin)</td>
            <td>P1</td>
        </tr>
        <tr>
            <td>4</td>
            <td>Visual Appearance</td>
            <td>User Interface for "Approve Signin" Feature Setup</td>
            <td>P1</td>
        </tr>
        <tr>
            <td>5</td>
            <td>Backend</td>
            <td>Update and Secure Legacy Portals with Advanced 2FA</td>
            <td>P1</td>
        </tr>
        <tr>
            <td>6</td>
            <td>Backend/Frontend</td>
            <td>Backup Method Implementation</td>
            <td>P1</td>
        </tr>
        <tr>
            <td>7</td>
            <td>Visual Appearance</td>
            <td>User Interface for Security Key Setup</td>
            <td>P2</td>
        </tr>
        <tr>
            <td>8</td>
            <td>Backend</td>
            <td>Integration of Security Key as a Login Option</td>
            <td>P2</td>
        </tr>
        <tr>
            <td>9</td>
            <td>Backend/Frontend</td>
            <td>Abnormal Activity Notification: Login IP History Tracking and Display</td>
            <td>P2</td>
        </tr>
        <tr>
            <td>10</td>
            <td>Backend</td>
            <td>Integration with App Push Notification Service</td>
            <td>P2</td>
        </tr>
        <tr>
            <td>11</td>
            <td>Backend</td>
            <td>Email Notification System</td>
            <td>P2</td>
        </tr>
        <tr>
            <td>12</td>
            <td>A/B Test</td>
            <td>Testing "Approve Signin" Feature and OTP Setup Complete Rate</td>
            <td>P3</td>
        </tr>
        <tr>
            <td>13</td>
            <td>A/B Test</td>
            <td>Testing User-Friendliness and Incentive of Overview Security Section</td>
            <td>P3</td>
        </tr>
        <tr>
            <td>14</td>
            <td>Internal Controls</td>
            <td>Monitoring and Feedback Tools</td>
            <td>P3</td>
        </tr>
        <tr>
            <td>15</td>
            <td>Backend/Frontend</td>
            <td>Privacy Data Deletion Features</td>
            <td>P3</td>
        </tr>
        <tr>
            <td>16</td>
            <td>Backend</td>
            <td>SMS Notification Integration</td>
            <td>P3</td>
        </tr>
 



### **Priority Definitions:**

- **P1 (Required for Launch)**: Essential features that are critical for the launch.
- **P2 (Expected for Launch)**: Important features that are planned for the launch but can be deferred if necessary.
- **P3 (Desired for Launch)**: Additional features that would enhance the product but are not crucial for the initial launch.

