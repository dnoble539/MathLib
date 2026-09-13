# probability-math

Wahrscheinlichkeits-/Kombinatorik-Kern (Binomialverteilung, `BigDecimal`-Arithmetik,
Newton-Nullstellensuche). Ausgelagert aus `TT-Siegwahrscheinlichkeit`; konsumiert von
`tt-siegwahrscheinlichkeit` und `magic-arena-ev`.

## Build

    gradlew.bat build

Benötigt ein JDK 21 (Gradle-Toolchain, wird aus den üblichen Speicherorten
z. B. `~/.jdks/` erkannt).

## Nutzung durch die App-Repos

Die App-Repos (`magic-arena-ev`, `tt-siegwahrscheinlichkeit`) binden diese
Library über [JitPack](https://jitpack.io) ein — JitPack baut den jeweils
getaggten Commit dieses GitHub-Repos on-demand und stellt ihn als
Maven-Artefakt bereit. Ein Checkout als Nachbarordner ist dafür **nicht**
mehr nötig.

In deren `build.gradle`:

    repositories {
        maven { url 'https://jitpack.io' }
    }

    dependencies {
        implementation 'com.github.dnoble539:MathLib:v1.1.0'
    }

(GroupId/ArtifactId ergeben sich bei JitPack aus GitHub-User/Repo-Name, nicht
aus `group`/`rootProject.name` hier.)

Für lokale Entwicklung ohne Internetzugriff auf JitPack kann alternativ ein
fester Stand eingefroren werden:

    gradlew.bat publishToMavenLocal

schreibt nach `~/.m2/repository/com/stats/probability-math/<version>/`; dazu
in den App-Repos `mavenLocal()` vor die JitPack-Zeile setzen.

## Versionierung

SemVer (`MAJOR.MINOR.PATCH`) in der `version`-Zeile in `build.gradle`.

Release-Ablauf:

1. `version` in `build.gradle` hochzählen.
2. Commit erstellen.
3. Git-Tag im Format `vMAJOR.MINOR.PATCH` setzen (muss zur `version` passen,
   da JitPack den Tag-Namen als Artefakt-Version verwendet) und pushen:

       git tag v1.0.1
       git push origin main --tags

4. In den App-Repos die Dependency-Zeile auf den neuen Tag anheben.

JitPack baut den Tag beim ersten Zugriff automatisch; ein Build-Status-Badge
kann optional unter https://jitpack.io/#dnoble539/MathLib eingesehen werden.
