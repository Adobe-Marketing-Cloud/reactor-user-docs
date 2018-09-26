

# Contributing Guide

This step-by-step guide will provide you with all you need to know to be an active contributor to the tutorials section of our user documentation. Our goal is to get as many of our users involved in providing example how-to content as possible. We're excited to have you contributing!



## Process

1. Check out the code from repo:

   ````
   git clone git@github.com:jiabingeng/sdk-v5-docs.git
   ````

2. Check out the content you want to update. For example, to update the "analytics" docs:

   ```
   git checkout -b analtyics origin/master
   
   ```

3. Work on the docs and then commit the code.

   ```
   git add *
   git commit -m 'something'
   ```

4. Push the code to the remote branch

   ````
   git push origin branchname
   ````


5. Create a Pull Request against **'master'** branch, and let Rekha or other team member reviewing it.

6. Fix all the comments, and once it gets approve and merged,you can view the docs on https://launch.gitbook.io/marketing-mobile-sdk-v5-by-adobe-documentation/



## Tools

- #### git

  You are free to choose whichever git tool you like, either command line or GUI tools.

- ##### Markdown

  There are a lot Markdown editors you can use, I personal prefer to use Typora https://typora.io/. And you can find the syntax in a [Markdown Cheat sheet](https://www.markdownguide.org/cheat-sheet/).




## File Structure

```
- README.md				The homepage of SDK documenation
- SUMMARY.md				Table of Contents defination
- CONTRIBUTING.md			Contributing guide
- TEMPLATE.md				md template
- release-notes				Releaes notes folder
	- README.md			Releaes notes page
- analytics				Folder for Analytics extension
	- ...					subpages of Analytics extension
- audience-manager			Folder for Audience Manager extension
	- ...
- .....					Other extensions
```






## Table of Contents

[SUMMARY.md](./SUMMARY.md) is the place where the ToC is defined. Check out https://toolchain.gitbook.com/pages.html to find more detail.



## Assets

To accommodate with Gitbook, all the Images should be put under folder `./gitbook/assets` folder. To better maintain and find images, follow the name pattern `chaptername-subpagename-imagename`. For example: `contributing-overview-tiger`

![tiger](.gitbook/assets/contributing-overview-tiger.jpeg)



## Code Block

You can define code block using three tilts, and to use the syntax highlighting, you'll need to specify the language that you're using. For example:

```java
​```
​```

​```java
​```

​```cpp
​```

​```objectivec
​```
```

Example:

```java

class Identity extends InternalModule {
	Identity(final EventHub hub, final PlatformServices platformServices) {
		super(EventDataKeys.Identity.MODULE_NAME, hub, platformServices);
	}
}
```

```cpp
namespace AdobeMarketingMobile {
    class Identity: public InternalModule {
        friend class TestableIdentity;
    public:
        static const std::string LOG_PREFIX;

    protected:

        /**
         * Create a new instance of Identity Module.
         *
         * @param log_prefix an identifier for this module used in log messages.
         */
        explicit Identity(const std::string& log_prefix);

    };
}
```
```objectivec
- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options {
    [self handleDeepLink:url];
    return YES;
}

```

## Tables

Unfortunately, long tables are not elegantly supported in GB. As a result, instead of using tables, list content by using bullet points.

## Event Pages

In the extensions section, each module will define the events that it dispatches and the events that it is listening for. Here is an example about how the events are described: [Event Description Template](EVENT_DESCRIPTION_TEMPLATE.md) 

**Important:** If you have **any** questions, please ask Rekha or Jiabin!
