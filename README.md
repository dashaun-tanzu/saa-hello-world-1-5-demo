[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]

# Spring Application Advisor Upgrade Example

## Description

This interactive demo showcases the power of Spring Application Advisor (SAA) by automatically upgrading a Spring Boot application from version 1.5.0 to 3.5.5. The demo provides a comprehensive comparison of performance improvements achieved through modern Spring Boot versions and Java runtime upgrades.

### What the Demo Does

1. **Environment Setup**: Automatically configures Java 8 and Java 17 environments using SDKMAN
2. **Baseline Measurement**: Clones and runs a Spring Boot 1.5.0 application with Java 8, measuring startup time and memory usage
3. **Application Analysis**: Uses Spring Application Advisor to analyze the existing application, capturing:
   - Build configuration metadata
   - Software Bill of Materials (SBOM) with component inventory
   - Git repository information
   - Tool versions and dependencies
4. **Automated Upgrade**: Generates and applies an upgrade plan that transforms the application to Spring Boot 3.5.5
5. **Performance Validation**: Runs the upgraded application with Java 17 and measures improvements
6. **Results Comparison**: Displays a side-by-side comparison showing:
   - Startup time improvements
   - Memory usage reductions
   - Percentage improvements in both metrics

### Key Benefits Demonstrated

- **Zero Manual Effort**: Complete upgrade from Spring Boot 1.5 → 3.5 with no manual code changes
- **Performance Gains**: Typically shows significant improvements in both startup speed and memory efficiency
- **Modern Java Features**: Leverages Java 17 optimizations and Spring Boot 3.x enhancements
- **Comprehensive Analysis**: Detailed insights into application composition and dependencies

The demo is designed for live presentations and includes interactive pauses, colored output, and timing measurements to create an engaging experience that highlights the value of automated Spring Boot upgrades.

## Prerequisites
- [Spring Application Advisor](https://enterprise.spring.io/spring-application-advisor)
  > Spring Enterprise Repository Access
- [SDKMan](https://sdkman.io/install)
  > i.e. `curl -s "https://get.sdkman.io" | bash`
- [Httpie](https://httpie.io/) needs to be in the path
  > i.e. `brew install httpie`
- bc, pv, zip, unzip, gcc, zlib1g-dev
  > i.e. `sudo apt install bc, pv, zip, unzip, gcc, zlib1g-dev -y`
- [Vendir](https://carvel.dev/vendir/)
  > i.e. `brew tap carvel-dev/carvel && brew install vendir`

## Quick Start
```bash
./demo.sh
```

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
