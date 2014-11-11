## Gradle - build automation evolved
#### Stig Kleppe-Jørgensen
FINN reise

Note:
Mitt navn er Stig og jeg jobber på FINN reise hvor vi har et ganske komplekst bygg.
Nevn noen eksempler på dette (test, module, feature, code check).
Derfor så vi behovet for et bedre byggverktøy, flere av oss som hadde erfaring med Gradle.
Holder på med et eksperiment for å finne ut hvordan gradle passer inn i FINN.
Hvem har brukt andre byggverktøy enn Maven? make, rake, ant?

----

## Why Gradle?

* Faster ([Maven](https://bamboo.finn.no/browse/TRAVELAPP-BUILDMASTER) vs [Gradle](https://bamboo.finn.no/browse/TRAVELAPP-BRANCHES))
* Easier maintenance

Note:
I hovedsak 2 grunner til å bytte: raskere og lettere vedlikehold
(web pom.xml -> 1060 linjer).

----

## Gradle &asymp; Ant + Maven + Groovy DSL

* Ant's power and flexibility
* Maven's conventions and dependency management
* Wrapped in a very nice DSL

Note:
En har tatt det beste fra ant og maven.
Fleksibiliteten gjør at en ikke låses fast i en måte å gjøre ting på, strukturer bygget slik du vil.
Samtidig har en konvensjoner å støtte seg på slik at ikke hjulet må finnes opp på nytt.

----

## Some features

* Proper multi-project support
* Incremental builds
* Dependency management extraordinaire
* Easy to write plugins
* Rich Groovy DSL
* Deep API
* Wrapper
* Daemon

Note:
Hva synes dere om multi-project-støtten i Maven?
Hva med å stå inne i et sub-project og bygge?
Grunnen til at Gradle er raskere er den fantastiske støtten for inkrementelle bygg.
Dette er bygget inn i kjernen og ikke noe hver plugin må implementere.
Transitiv eller ikke, globale excludes + mange andre muligheter.
Lokal cache er _mye_ bedre, hashet på innhold og tilhøriget, multiprosess-støtte
Ny funksjonalitet kan skrives direkte inn i byggskriptet i Groovy, flyttes ut i buildSrc/ eller lages plugin av.
Rik DSL med masse hooks i hele livssyklusen gjør det veldig kraftfult og enkelt å styre konfigurasjon hele veien ned til kjernen.
Med wrapper trenger en ikke å ha installert Gradle, kan spesifisere en spesifikk versjon, sjekke inn "all" konfig for prosjektet

----

### The simplest build script

```java
apply plugin: 'java'
```

----

### Having some dependencies

```java
apply plugin: 'groovy'

repositories {
    mavenCentral()
}

dependencies {
    compile 'org.slf4j:slf4j-api:1.7.5'

    testCompile 'junit:junit:4.11'
}

```

----

## Documentation

* User guide
* DSL
* Java/Groovydoc
