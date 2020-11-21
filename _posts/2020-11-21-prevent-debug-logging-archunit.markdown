---
layout: post
title:  "Prevent debug logging with archunit"
date:   2020-11-21 22:00:19 +0200
categories: tech
comments: true
---
In my new team we have weekly <abbr title="pair programming but with more people">mob programming</abbr> sessions where we usually refactor some part of our codebase. These sessions also really helpful for enriching our coding style / design pattern conventions. One of the new conventions is "do not log anything with `debug` log level". We simply just don't care about them. Actually, in production the log level is set to `info`, and we never missed the debug logs. It's just dead code.

Removing all of them is easy, but its nice to take another step forward and think about it, how we can prevent such dead code to reappear in the future (eg. by programmers who couldn't participate our mob session). The easy (?) way to achieve this is just writing this down in some markdown file / confluence page etc. The clever way on the other hand is to write some automation.

Probably there are endless ways to automate this check somehow, but in this post I will show how to do it in [archunit](https://www.archunit.org/). Archunit is a free, but very powerful tool to enforce and validate architecture and design patterns, coding style and more in java projects. 

It can be used in your already set up unit testing framework, you just have to import some dependency and its good to go. There are lots of good articles out there about the quick start process, check out the linked page. If its done, just create a new unit test with this content:

```java
import static com.tngtech.archunit.core.domain.JavaCall.Predicates.target
import static com.tngtech.archunit.core.domain.JavaClass.Predicates.assignableTo
import static com.tngtech.archunit.core.domain.properties.HasName.Predicates.name
import static com.tngtech.archunit.core.domain.properties.HasOwner.Predicates.With.owner
import static com.tngtech.archunit.lang.syntax.ArchRuleDefinition.classes
import static com.tngtech.archunit.lang.syntax.ArchRuleDefinition.noClasses

// ...

JavaClasses contactClasses

setup() {
    myClasses = new ClassFileImporter()
        .withImportOption(ImportOption.Predefined.DO_NOT_INCLUDE_TESTS)
        .importPackages("my.base.package")
}

// ...

noClasses()
    .should().callMethodWhere(
        target(name("debug"))
        .and(target(owner(assignableTo(Logger.class)))))
.check(myClasses)
```

This example expects that you are using Slf4J or something similiar. The `check` method will throw an `java.lang.AssertionError` if the check failed.

That's it for now, but expect to come similiar posts to this one in the future.