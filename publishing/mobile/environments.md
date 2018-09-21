# Environments

Extensions, rules, and data elements are building blocks. When you want to make your application do something, these building blocks are added to libraries and then a library is "built" into a build.

When you create a library, you must assign it to an environment. 

## Create an Environment

New properties are created with three environments: one Development, one Staging, and one Production. This is enough to run the publishing workflow. If desired, you may add additional Development environments. This is most common on larger teams with multiple developers working on different projects at the same time.

1. Open the Environments tab.
2. Click Create New Environment.
3. Select the type of environment you want to create.
   * Development

     The environment where you create and edit, events, configurations, and so on.

   * Staging

     The environment where you test and approve your changes.

   * Production

     The environment where your embed codes are placed in the pages or applications that are available to the public.
4. Select your adapter.
5. Click Save.
6. Repeat for each environment in your development, approval, and publishing change.

For mobile apps, remember the following information:

* The Dev, Stage, and Prod environments are created automatically.
* You can only create multiple Dev environments. 

After the environments are created, you are ready to publish.

