After a few years of running applications using Gradle, I started seeing the `implementation` dependency configuration in a lot of projects. Coming from mostly legacy applications running Gradle v3.5, I had not had the opportunity to use it yet.

The latest configurations provided by the `java` and `java-library` plugins offer some much-improved granularity for how application dependencies are exposed to downstream consumers. Previously, the only option for compile-time dependencies which are also required at runtime was the `compile` configuration. Now we can leverage `implementation` and `api` (if you are using `java-library`).

##### Let's get to defining exactly how these are different:

###### `compile`
- Compile time dependencies
- Exposed to downstream consumers of the project

###### `implementation`
- Compile time dependencies
- Not exposed to any downstream consumers

###### `api`
- Compile time dependencies
- Exported to the public API to downstream consumers

*Remember:* the `api` dependency configuration only exists in the `java-library` plugin.

This separation of concerns is a great improvement and I'm happy to have more control over what transitive dependencies I might create for others.

# 🐾