# RabbitMQ for Pivotal CF docs

### Branch Management

**master** - all documentation for the next unreleased version of **RabbitMQ** should land in master. Any changes on this branch will not be displayed publicly until a **minor** branch is cut, and an update to [docs-book-pcfservices][docs-book-pcfservices] is done (To be documented).

**1.7-live** - current branch for documentation that is assumed/expected to be live on [docs.pivotal.io/rabbitmq-cf/1-7](http://docs.pivotal.io/rabbitmq-cf/1-7/).

**1.6-live** - current branch for documentation that is assumed/expected to be live on [docs.pivotal.io/rabbitmq-cf/1-6](http://docs.pivotal.io/rabbitmq-cf/1-6/).

**1.5-live** - current branch for documentation that is assumed/expected to be live on [docs.pivotal.io/rabbitmq-cf/1-5](http://docs.pivotal.io/rabbitmq-cf/1-5/).

[docs-book-pcfservices]: https://github.com/pivotal-cf/docs-book-pcfservices/blob/master/config.yml

### Staging Environment

When a commit is made into any of the above branches, the documentation is deployed by [this concourse build][docs-staging-deploy]. All the supported
versions will be accessible on the [staging website][docs-staging] One caveat is
that the **master** docs are deployed to an [obfuscated url path][docs-staging-master].

[docs-staging-deploy]: https://p-concourse.wings.cf-app.com/teams/system-team-docs-docs-1-88aa/pipelines/cf-current/jobs/pcfservices-staging
[docs-staging-master]: http://docs-pcf-staging.cfapps.io/rabbitmq-cf-d34379b0-a290-47c7-bc6c-c45a9adfa8c7/
[docs-staging]: http://docs-pcf-staging.cfapps.io/rabbitmq-cf-d34379b0-a290-47c7-bc6c-c45a9adfa8c7/

### Making Your Documentation Changes Live

So... you've got your documentation merged into a **live** branch, and the documentation is reflected on the staging site
but not on the live website http://docs.pivotal.io/rabbitmq-cf/index.html? You probably just need to wait for the next 
deployment to happen or ask for a push-to-production in [\#pcf-docs](https://pivotal.slack.com/messages/pcf-docs/). If there's
no hurry, it'll get deployed the next time documentation is pushed to production.

### Tag Management

We do not need to maintain older versions of the documentation so we're electing to not use tags to snapshot the state of the documentation for each previous patch version.

### Contributing Documentation

If there's some documentation to add for an unreleased patch version of RabbitMQ then create a branch off of the **live** branch you intend to modify and create a Pull Request against that branch. Once the version that change is targeting is released, the Pull Request can be merged and will be live the next time a documentation deployment occurs.

If the documentation is meant to be target several released versions, then you'll need to create a Pull Request for each individual minor version.

### Releasing a New Minor Version

Since **master** is the latest and greatest documentation, the process would be to cut a **x.x-live** branch for the version that **master** was targeting during that time. A corresponding section in **config.yml** in the [docs-book-pcfservices][docs-book-pcfservices] repository would also need to be made.

After this point, **master** will then be the target for the next version of the RabbitMQ product tile.

