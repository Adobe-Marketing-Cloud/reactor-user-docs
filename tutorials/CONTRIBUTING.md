# **Contributing Overview**

This step-by-step guide will provide you with all you need to know to be an active contributor to the tutorials section of our user documentation. Our goal is to get as many of our users involved in providing example how-to content as possible. We're excited to have you contributing!

As you may or may not know, Adobe Launch uses the GitBook platform to display its documentation. It can be found [here](https://docs.adobelaunch.com/ "Adobe Launch Documentation"). 

**Found a bug or issue? Submit it [here](https://github.com/Adobe-Marketing-Cloud/reactor-user-docs/issues/new "Report new bug or issue").**

Let's jump right in!
<br><br>
# Good Tutorial Practices
>*Please keep these tips in mind while building your tutorial page*
- Have a descriptive and succinct title! It's the best way for others to find exactly what they're looking for. Perhaps even include a short text description of what your tutorial aims to achieve.
- Videos and screenshots are one of the best ways to provide instruction, and we highly encourage using them. However, be careful that your media does not disclose any sensitive information such as passwords, tokens, or keys.
- Create your tutorial in the corresponding sections such as Publishing, Data Elements, or Other. This will help users find exactly what they're looking for. 

## 1. **Read Required Contributor Material**
As with any project, it's best to be prepared before beginning. Read the below information to familiarize yourself with contribution policies and guidelines.

> ### Code Of Conduct
---

> This project adheres to the Adobe [code of conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior to Grp-opensourceoffice@adobe.com.

> ### Contributor License Agreement
---

> All third-party contributions to this project must be accompanied by a signed contributor license. This gives Adobe permission to redistribute your contributions as part of the project. Sign our [CLA](http://opensource.adobe.com/cla.html). You only need to submit an Adobe CLA one time, so if you have submitted one previously, you are probably good to go!

> ### Code Reviews
---

> All submissions should come in the form of pull requests and need to be reviewed by project committers. Read [GitHub's pull request documentation](https://help.github.com/articles/about-pull-requests/) for more information on sending pull requests.

## 2. **Sign Our CLA (Contributor License Agreement)**

>In order to contribute to our documentation, you **MUST** sign the contributor license agreement, also known as the CLA. If you've signed and submitted one previously, you're good to go! Otherwise, visit [here](http://opensource.adobe.com/cla.html) to get signing.

## 3. **Clone the Repository**

>1. Open your terminal and navigate to the place you want to store the project.
>2. Copy this command and paste it into the terminal.  
```git clone https://github.com/Adobe-Marketing-Cloud/reactor-user-docs.git```
>3. Open the project in your editor. 

## 4. **Checkout to a New Branch**

>In your terminal, run  
```git checkout -b [name-of-your-branch]```

## 5. **Create Your Content**  

>You are now set to begin creating your tutorial page. Be sure your new file title is descriptive, succinct, and is a .md file.  
**Good title**: "creating-a-new-rule.md"   
MD stands for markdown. If you are unfamiliar with .md files or markdown, you can learn more [here](https://guides.github.com/features/mastering-markdown/). A template.md file is located in the tutorials folder to help you get started. 

## 6. **Create a New Pull Request**

>Once you've finished with your tutorial and are happy with the changes, it's time for a pull request! This is basically a request to have your changes added to the live site. It's important to note that any changes outisde of your new tutorial files will **not** be accepted.
>1. Open your terminal to the reactor-user-docs project. 
>2. Enter  
 ```git add .```  
 and press enter.
>3. Enter  
```git commit -m "New tutorial"```  
and press enter.
>4. Enter  
```git push origin [name-of-your-branch]```
>5. Return to https://github.com/Adobe-Marketing-Cloud/reactor-user-docs. There should now be a green button that says "Create pull request". If there's not, click on the gray button that says "New pull request." You may choose to leave a comment, then click "Create pull request".
>You may receive requested changes after your pull request is reviewed. After those changes are made, follow the steps 1-4 again. Once everything is satisfactory, your pull request will be merged into the master branch.

>>>**Please note that there will be no expectations on how long it will take to be approved and merged.*
