# Mar 2022
### 4 Mar

1. How to update dependencies used in a transitive dependency

    Look at the example below.

    ```implementation 'com.github.bumptech.glide:okhttp3-integration:4.1.13'```

    This uses an outdated dependency `com.squareup.okhttp3.okhttp:3.12.1`, but the latest is `4.9.3`.   
Therefore, we can follow the steps below.

    ```
    implementation 'com.github.bumptech.glide:okhttp3-integration'

    constraint {
        implementation("com.github.bumptech.glide:okhttp3-integration:4.13.1") {
            because 'Previous version may cause security issues'
        }

        implementation("com.squareup.okhttp3:okhttp:4.9.3") {
            because 'Applied the latest one'
        }
    }
    ```
### 11 Mar

1. How to use Nexus (internal repo)
   
   ```sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target```
   
   In order to avoid this message, We have to add certification of nexus server to Android Studio
   Go to jre folder of System, and use keytools like below 
   
   ```./bin/keytool -importcert -file /path/to/your/certificate/my-root-ca-cert.cer -keystore ./jre/lib/security/cacerts -storepass changeit -noprompt```
   
   Just in case, Go and find server certification in Android Studio, and add the optional certificate.
   
   Lastly restart Android studio.
   
### 16 Mar

1. Adding Firebase into `build.gradle` when the gradle version is above 7.3

    ```
    // Top-level build file where you can add configuration options common to all sub-projects/modules.
    buildscript {
        dependencies {
            classpath 'com.google.dagger:hilt-android-gradle-plugin:2.38.1'
            classpath 'com.google.gms:google-services:4.3.10'
        }
    }

    plugins {
        id 'com.android.application' version '7.1.2' apply false
        id 'com.android.library' version '7.1.2' apply false
        id 'org.jetbrains.kotlin.android' version '1.6.10' apply false
    }
    ...
    ```
    Cause `google()` is already defined in `settings.gradle`, so we don't need to declare that `google()` in the project level `build.gradle`.
    See below.
    
    ```
    pluginManagement {
        repositories {
            gradlePluginPortal()
            google()
            mavenCentral()
        }
    }
    
    dependencyResolutionManagement {
        repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
        repositories {
            google()
            mavenCentral()
        }
    }
    ```

## 26 Mar 
1. `Startup Library` has used `WorkManager` internally so if we try to use it in `create()` of subclassed `Initializer`, it will crash.
