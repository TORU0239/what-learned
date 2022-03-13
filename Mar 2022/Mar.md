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
