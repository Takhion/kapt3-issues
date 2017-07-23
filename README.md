This project shows 2 issues with kapt3.

To make the results consistent, I suggest to run a "deep clean" when building, like so:
```bash
$ rm -rf ./build ./*/build && ./gradlew clean build
```
You'll notice if the annotation processor is called correctly by the following log:
```
warning: *** AP RUNNING ***
```
## [Issue 1](https://youtrack.jetbrains.com/issue/KT-19178)
By enabling kapt3 in the `app` project (uncomment [here](app/build.gradle#L2)) the annotation processor isn't run unless it's also used as a `compile` dependency (uncomment [here](app/build.gradle#L11)).

## [Issue 2](https://youtrack.jetbrains.com/issue/KT-19179)
By enabling kapt3 in the `processor` project (uncomment [here](processor/build.gradle#L2)) the `@AutoService` annotation processor won't be run and as a result the correct `META-INF` file won't be generated.
