# HowtoBazelAndroid
Build Android apps using Bazel

Prior to creating this I had no knowledge of Bazel other than it's name, and I'm still not knowledged in it. 
This is just an example to help me understand it better over time. 

### Introduction

This repository is a newly generated Android Studio project with a near blank activity.

Bazel (`version 0.1.4-jdk7`) is setup to compile this project. 

### Initial thoughts

#### Installation

[Installation](http://bazel.io/docs/install.html) was a breeze. 
Obviously it is not as 'simple' as the [Gradle Wrapper](https://docs.gradle.org/current/userguide/gradle_wrapper.html). The Gradle Wrapper is nice if you're not normally an Android Developer, you litterally just call `./gradlew <task>` and you're building. Ignoring that fact, setting up bazel was easy, and if you were to upgrade your app's install guide it would be a one-liner addition.

#### Conventions
The conventions are nice. The only things required to get up and going with Bazel is a [`WORKSPACE`](http://bazel.io/docs/build-ref.html#workspaces), and `BUILD` files.

- The `WORKSPACE` file is located in your project root and is used for Bazel to contextualize itself in the subdirectories for the `BUILD` files.

- The `BUILD` files are closer to the actual thing you want to build. So in this case, `app/`. 

I can see great benefit on this convention. This convention makes it pretty simple to split off subprojects, or in the opposite way of forming monorepositories.

#### Bazel and Gradle don't play nicely.

If you're hoping to continue to use Gradle and slowly migrate into Bazel, if you don't have `git config core.ignorecase` set to `false` you're going to have a bad time.

Bazel and Gradle both use the `/build/i` filename. 

- Bazel's `BUILD` is used to hold build targets

- Gradle's `build/` is the directory built targets get put.

So if `git config core.ignorecase == false`, Gradle is going to overwrite your Bazel `BUILD` file.
Otherwise, `git config core.ignorecase == true` Gradle won't be able to overwrite the Bazel `BUILD` file and die.

This is a serious issue with convention. As far as I found, changing what Bazel looks at for a `BUILD` file is not possible.

### So, is it fast? 

|                                         | Bazel         | Gradle        |
| --------------------------------------- | ------------- | ------------- |
| `build` / `assembleDebug` from `clean`  | TODO          | TODO          |
| `build` / `assembleDebug` with cache    | TODO          | TODO          |
| `install`                               | TODO          | TODO          |
