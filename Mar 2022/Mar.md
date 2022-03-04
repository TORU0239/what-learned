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
