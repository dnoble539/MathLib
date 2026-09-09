# probability-math

Wahrscheinlichkeits-/Kombinatorik-Kern (Binomialverteilung, `BigDecimal`-Arithmetik,
Newton-Nullstellensuche). Ausgelagert aus `TT-Siegwahrscheinlichkeit`; konsumiert von
`tt-siegwahrscheinlichkeit` und `magic-arena-ev`.

## Build

    gradlew.bat build

Benötigt ein JDK 19 (Gradle-Toolchain, wird aus den üblichen Speicherorten
z. B. `~/.jdks/` erkannt).

## Nutzung durch die App-Repos

Die App-Repos binden diese Library per Gradle Composite Build ein
(`includeBuild '../probability-math'` in deren `settings.gradle`) — dafür muss
dieser Ordner als Nachbarordner ausgecheckt sein.

Alternativ einen festen Stand einfrieren:

    gradlew.bat publishToMavenLocal

schreibt nach `~/.m2/repository/com/stats/probability-math/1.0/`.

## Versionierung

Eine `version`-Zeile in `build.gradle`. Nur hochzählen, wenn bewusst ein altes
JAR in `~/.m2` behalten werden soll. Kein SemVer-Regelwerk, keine CI.
