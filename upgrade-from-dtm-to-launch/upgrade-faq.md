# Upgrade FAQ

### What does the Launch Upgrade do? {#what-does-the-launch-upgrade-do}

The Launch Upgrade reads your DTM property and attempts to make a complete copy of that property in Launch. The resulting Launch property is structured to mimic the on-page behavior of your DTM property as closely as possible. To read about differences in structure, see [Upgrade Preparation Guide](upgrade-preparation-guide.md).

When the upgrade is complete, a new property appears in Launch. A link to the new property is created. If the upgrade doesn't work, partially completed operations are deleted and an error message explains as much as possible about what went wrong. In some cases, error messages inform you that you can modify your DTM property and try the upgrade again.

The upgrade does not make any changes to your DTM property.

### How do I start the upgrade? {#how-do-i-start-the-upgrade}

Log in to DTM through the Experience Cloud, select your DTM property, then click **Upgrade to Launch**.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LAxHla2X11_-j5Ak32l%2F-LFJyF3ou47m7oJeaH9w%2F-LFJyJz_MpGT-AtrmEOs%2Fupgrade_to_launch.png?alt=media&token=5f5d841c-dcd2-4e91-a748-716bdc82d584)

### Where is my upgrade button? {#where-is-my-upgrade-button}

During this initial rollout phase of the Upgrade functionality, we are making it available after you opt-in. It is impossible to for us to test emitted Launch builds in all of the myriad scenarios and environments where our customers deploy it.

While the functionality is still brand new, we want to make sure that those who are using it know what they are signing up for and have agreed to do thorough testing of the emitted builds in a dev state and let us know any issues they uncover.

You can opt-in by providing your Adobe Org ID and agreeing to rigorous testing [here](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=69K2XN).

### Why is my upgrade button greyed out? {#why-is-my-upgrade-button-greyed-out}

If you mouse over the button it will tell you, but generally, there are a few reasons.

1. Your Property is Disabled. Enable the DTM Property first before you try to Upgrade.
2. You did not sign in through the Experience Cloud. Your DTM Company has to be connected to the same Experience Cloud Org as your Launch Company, and we can't tell if you don't sign in through the Experience Cloud. Login through the Experience Cloud and try again.
3. You are not a DTM **Admin**. You must be a DTM **Admin** to perform the Upgrade. Ask your admin nicely to Upgrade for you. Or ask even more nicely if you'd like them to make you an Admin and do it yourself.
4. You don't have the **Manage Properties** right in Launch. Ask your Org Admin \(or a Launch Product Admin\) to add you to a Product Profile with the **Manage Properties** right.

### What does the recommended upgrade process look like? {#what-does-the-recommended-upgrade-process-look-like}

1. Complete the upgrade process in DTM.
2. Go to Launch and make a new Development library with all your new changes.
3. Test thoroughly in your Launch Development environment.
4. Adjust data elements and rules as desired.
5. Promote changes through to the Launch Production environment.
6. \(Optional\) Disable the DTM property any time after completing Step 1.

### How should I get ready to upgrade? {#how-should-i-get-ready-to-upgrade}

Not everything that you can do in DTM is compatible with Launch. A list of these items is available in the [preparation guide](upgrade-preparation-guide.md). Make any necessary changes to your DTM property before you attempt the upgrade.

### What do I do if the upgrade doesn't work? {#what-do-i-do-if-the-upgrade-doesnt-work}

The upgrade is expected to succeed in nearly every scenario. There are a few reasons that it may fail:

1. You don't have the correct permissions. If the upgrade fails for this reason, correct any permissions issues and try again, or ask someone with the appropriate permissions to perform the Upgrade for you.
2. Your property has configuration issues. If the Upgrade fails for this reason, DTM informs you that you have property configuration issues. Please check the [Preparation Guide](upgrade-preparation-guide.md) and try again.

Failures for any other reason are rare. If your upgrade fails for any other reason, please contact Client Care and provide your DTM Company and Property Name. Client Care will troubleshoot the issue.



