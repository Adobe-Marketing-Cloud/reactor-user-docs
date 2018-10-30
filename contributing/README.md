# Tutorials

This step-by-step guide provides all you need to know to be an active contributor to the tutorials section of our user documentation. The goal is to get as many users involved in providing example how-to content as possible. We're excited to have you contributing!

Adobe Launch uses the GitBook platform to display its documentation. It can be found [here](https://docs.adobelaunch.com/).

**Found a bug or issue? Submit it** [**here**](https://github.com/Adobe-Marketing-Cloud/reactor-user-docs/issues/new)**.**

Let's jump right in!

## Good Tutorial Practices

### Please keep these tips in mind while building your tutorial page

* Have a descriptive and succinct title. It's the best way for others to find exactly what they're looking for. Perhaps even include a short text description of what your tutorial aims to achieve.
* Videos and screenshots are one of the best ways to provide instruction, are highly encouraged. However, be careful that your media does not disclose any sensitive information such as passwords, tokens, or keys.
* Create your tutorial in the corresponding sections such as Publishing, Data Elements, or Other. This will help users find exactly what they're looking for.
* Feel free to reference our [example tutorial](https://docs.adobelaunch.com/contributing/template) for guidance on how to format yours.

## 1. Read Required Contributor Material

As with any project, it's best to be prepared before beginning. Read the information below to familiarize yourself with contribution policies and guidelines.

### Code Of Conduct

This project adheres to the Adobe [code of conduct](https://github.com/Adobe-Marketing-Cloud/reactor-user-docs/tree/08d765fa041ac11be27a77e312baa1ab79aa59c0/tutorials/CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior to Grp-opensourceoffice@adobe.com.

### Contributor License Agreement

All third-party contributions to this project must be accompanied by a signed contributor license. This gives Adobe permission to redistribute your contributions as part of the project. Sign our [CLA](http://opensource.adobe.com/cla.html). You only need to submit an Adobe CLA one time, so if you have submitted one previously, you are probably good to go.

### Code Reviews

All submissions should come in the form of pull requests and need to be reviewed by project committers. Read [GitHub's pull request documentation](https://help.github.com/articles/about-pull-requests/) for more information on sending pull requests.

## 2. Sign the CLA \(Contributor License Agreement\)

In order to contribute to our documentation, you **MUST** sign the contributor license agreement, also known as the CLA. If you've signed and submitted one previously, you're good to go. Otherwise, visit [here](http://opensource.adobe.com/cla.html) to get signing.

## 3. Clone the Repository

If you're new to Github, check out their handy guides to get started: [https://guides.github.com/](https://guides.github.com/).

1. Open your terminal and navigate to the place you want to store the project.
2. Copy this command and paste it into the terminal.

   ```bash
    git clone https://github.com/Adobe-Marketing-Cloud/reactor-user-docs.git
   ```

3. Open the project in your editor.

## 4. Checkout to a New Branch

In your terminal, run:

```bash
git checkout -b [name-of-your-new-branch]
```

## 5. Create Your Content

You are now set to begin creating your tutorial page. Be sure your new file title is descriptive, succinct, and is a .md file.

```text
Good title: "creating-a-new-rule.md"
```

MD stands for markdown. If you are unfamiliar with .md files or markdown, you can learn more [here](https://guides.github.com/features/mastering-markdown/). Unfortunately, markdown does not support embedding videos. If you need to embed a video, please leave a comment in the location you would like your video with the following format:

```text
// Embed video here. Link: https://www.youtube.com/watch?v=eZBlRkF0-tolist=PLVkhvRpDxnn8aDsk9mW_wVufaOKJRK-Ls&index=2
```

We will embed the video for you in the location of your comment when your contribution is merged. A [TEMPLATE.md](template.md) file is located in the tutorials folder to help you get started.

Feel free to include some personal information about yourself. This would be a great place for a link to your github, twitter, instagram, or all of the above.

## 5. Add Your Tutorial to the SUMMARY.md

To have your tutorial show up within the documentation navigation, you'll need to add some info to the SUMMARY.md file in the root folder of reactor-user-docs.

If, for example, you create a tutorial about how to create a new rule, follow these steps:

1. Open the [SUMMARY.md](https://github.com/Adobe-Marketing-Cloud/reactor-user-docs/tree/08d765fa041ac11be27a77e312baa1ab79aa59c0/SUMMARY.md) file.
2. In the tutorials section, create a new line under the Rules section.
3. Tab over once, and write markdown for the link. The link to the tutorial would look like this.

   `* [Create a New Rule](tutorials/create-a-new-rule.md)`

The text between the brackets is how the name of your tutorial will show up in the navigation. Between the parenthesis is the path to your tutorial. The path will always be `tutorials/name-of-your-tutorial-file`. Be sure to include the asterisk.

## 6. Create a New Pull Request

Once you've finished with your tutorial and are happy with the changes, it's time for a pull request! This is basically a request to have your changes added to the live site. It's important to note that any changes outisde of your new tutorial files will **not** be accepted.

1. Open your terminal and navigate to the reactor-user-docs project.
2. Enter

   ```bash
    git add .
   ```

   then

   ```bash
    git commit -m "New tutorial"
   ```

   then

   ```bash
    git push origin [name-of-your-branch]
   ```

3. Return to [https://github.com/Adobe-Marketing-Cloud/reactor-user-docs](https://github.com/Adobe-Marketing-Cloud/reactor-user-docs). There should now be a green button that says "Create pull request." If there's not, click on the gray button that says "New pull request." You may choose to leave a comment, then click "Create pull request." You may be asked to make changes after your pull request is reviewed. After those changes are made, repeat the steps 1-4 under "Create a New Pull Request." Once everything is satisfactory, your pull request will be merged into the master branch.

   _\*Please note that there will be no expectations on how long it will take for your contribution to be approved and merged._

