[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]

![Demo](demo.gif)

# Spring Application Advisor Upgrade Example

A scripted live demo that takes a Spring Boot 1.5 / Java 8 app, uses [Spring Application Advisor](https://enterprise.spring.io/spring-application-advisor) to upgrade it to Spring Boot 4.0 / Java 21, and prints a startup-time and memory comparison table at the end.

## What the demo does

1. Clones [`dashaun/hello-spring-boot-1-5`](https://github.com/dashaun/hello-spring-boot-1-5) into `upgrade-example/`.
2. Downloads the pinned `ADVISOR_VERSION` of the advisor CLI from the Spring Enterprise Maven repo into `upgrade-example/cli-binary/`.
3. Runs the app on **Java 8 / Spring Boot 1.5** and records startup time and memory.
4. Captures a build config with `advisor build-config get`, then applies an upgrade plan via `advisor upgrade-plan apply --squash 17`.
5. Re-runs the app on **Java 21 / Spring Boot 4.0** and records metrics.
6. Prints a colored comparison table of startup time and memory savings.

## Quick Start

```bash
export ADVISOR_VERSION=1.6.2   # pin the Spring Application Advisor CLI version
./demo.sh
```

> **Heads up:** the script kills every running `java` process on the host before starting — it assumes any JVM is a leftover Spring Boot from a prior run. Don't run it on a machine with unrelated JVMs you care about.

## Prerequisites

- [Spring Application Advisor](https://enterprise.spring.io/spring-application-advisor) — the demo downloads the pinned `ADVISOR_VERSION` CLI from the Spring Enterprise Maven repo per run (no system install needed), so your `~/.m2/settings.xml` must already be authenticated against that repo.
- [SDKMAN](https://sdkman.io/install) — `curl -s "https://get.sdkman.io" | bash`. Java versions are declared in [`.sdkmanrc`](./.sdkmanrc); install missing ones with `sdk env install` from the repo root.
- [HTTPie](https://httpie.io/) — `brew install httpie`.
- [Vendir](https://carvel.dev/vendir/) — `brew tap carvel-dev/carvel && brew install vendir`.
- Maven (`mvn`) and `tar` — used to fetch and extract the advisor CLI.
- `bc`, `pv`, `zip`, `unzip`, `gcc`, `zlib1g-dev` — e.g. `sudo apt install -y bc pv zip unzip gcc zlib1g-dev` on Debian/Ubuntu.

## Java Versions

Java versions used by the demo are declared in [`.sdkmanrc`](./.sdkmanrc) — one `java=<version>` line per major version. `demo.sh` reads them from there at startup, and SDKMAN will also pick them up automatically if you have `sdkman_auto_env=true`. To change a Java version, edit `.sdkmanrc`; no changes to `demo.sh` are required.

## Attributions
- [Demo Magic](https://github.com/paxtonhare/demo-magic) is pulled via `vendir sync`

## Related Videos

- https://www.youtube.com/live/qQAXXwkaveM?si=4KunXZaretBrPZs3
- https://www.youtube.com/live/ck4AP7kRQkc?si=lDl203vbfZysrX5e
- https://www.youtube.com/live/VWPrYcyjG8Q?si=z7Q2Rm_XOlBwCiei

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[forks-shield]: https://img.shields.io/github/forks/dashaun-tanzu/saa-hello-world-1-5-demo.svg?style=for-the-badge
[forks-url]: https://github.com/dashaun-tanzu/saa-hello-world-1-5-demo/forks
[stars-shield]: https://img.shields.io/github/stars/dashaun-tanzu/saa-hello-world-1-5-demo.svg?style=for-the-badge
[stars-url]: https://github.com/dashaun-tanzu/saa-hello-world-1-5-demo/stargazers
[issues-shield]: https://img.shields.io/github/issues/dashaun-tanzu/saa-hello-world-1-5-demo.svg?style=for-the-badge
[issues-url]: https://github.com/dashaun-tanzu/saa-hello-world-1-5-demo/issues
