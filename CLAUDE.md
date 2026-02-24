# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Spring Application Advisor (SAA) demonstration repository that showcases upgrading a Spring Boot application from version 1.5.0 to 3.5.5. The demo uses automated scripts to demonstrate the upgrade process using Spring Application Advisor tools.

## Architecture

- **Demo Script**: `demo.sh` - Main orchestration script that runs the entire upgrade demonstration
- **Vendir Configuration**: `vendir.yml` - Manages external dependencies (demo-magic library)
- **Sample Application**: `upgrade-example/` - Contains a simple Spring Boot application that gets upgraded during the demo
- **Dependencies**: Uses demo-magic for interactive presentation and various system tools

## Key Commands

### Running the Demo
```bash
./demo.sh
```
This is the primary command that:
- Sets up Java environments (Java 8 and 17 via SDKMAN)
- Clones a Spring Boot 1.5 application
- Runs Spring Application Advisor analysis and upgrades
- Demonstrates performance comparisons between versions

### Dependency Management
```bash
vendir sync
```
Updates external dependencies defined in `vendir.yml` (currently demo-magic library)

### Spring Boot Application Commands (within upgrade-example/)
```bash
# Build and test
./mvnw clean package

# Run application
./mvnw spring-boot:run

# Run tests
./mvnw test

# Start application in background
./mvnw spring-boot:start -Dfork=true

# Stop background application
./mvnw spring-boot:stop
```

### Spring Application Advisor Commands
```bash
# Capture application metadata
advisor build-config get

# Generate upgrade plan
advisor upgrade-plan get

# Apply upgrades
advisor upgrade-plan apply --squash 16
```

## Prerequisites

The demo requires several tools to be installed:
- SDKMAN (for Java version management)
- HTTPie (for API testing)
- Vendir (for dependency management)
- Standard Unix tools: bc, pv, zip, unzip, gcc, zlib1g-dev
- Git
- Spring Application Advisor (requires Spring Enterprise Repository access)

## Demo Flow

1. **Setup**: Initialize SDKMAN, install Java versions, clean up any running processes
2. **Baseline**: Run Spring Boot 1.5 with Java 8, measure performance
3. **Analysis**: Use Spring Application Advisor to analyze the application
4. **Upgrade**: Apply automated upgrades to Spring Boot 3.5
5. **Validation**: Run upgraded application with Java 17, measure performance improvements
6. **Comparison**: Display side-by-side performance metrics

## Files Structure

- `demo.sh` - Main demo orchestration script with timing and performance measurement
- `vendir.yml` - External dependency configuration
- `vendir.lock.yml` - Locked dependency versions
- `upgrade-example/` - Sample Spring Boot application directory
- `upgrade-example/pom.xml` - Maven configuration (gets modified during demo)
- `upgrade-example/src/main/java/` - Java source code
- `.idea/` - IntelliJ IDEA project files