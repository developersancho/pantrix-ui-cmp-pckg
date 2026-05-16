 # pantrix-ui-cmp-pckg
  
  [![Source](https://img.shields.io/badge/source-developersancho%2FPantrixUI-blue?logo=github)](https://github.com/developersancho/PantrixUI)
  [![Docs](https://img.shields.io/badge/docs-pantrixui.com-7c5cfc)](https://developersancho.github.io/PantrixUI/)
  [![License](https://img.shields.io/badge/license-Apache%202.0-green)](https://github.com/developersancho/PantrixUI/blob/main/LICENSE)
  [![Version](https://img.shields.io/badge/version-1.0.0-success)](#available-artifacts)

  > **This repository hosts the published Maven artifacts for PantrixUI only.**
  > Source code, issue tracker, documentation, and the project README live at **[developersancho/PantrixUI](https://github.com/developersancho/PantrixUI)**.

  PantrixUI is a production-ready **Kotlin Multiplatform** UI component library built with **Compose Multiplatform** — 65+ components, 10 chart types, 19 theme
  presets, 70 semantic color tokens, and 19 icon packs across Android, iOS, Desktop, and Web.

  ---

  ## Quick Start
  
  ### 1. Authenticate to GitHub Packages
  
  GitHub Packages requires authentication **even for public packages**. Create a Personal Access Token at GitHub → **Settings → Developer settings → Personal 
  access tokens (classic)** with the `read:packages` scope, then store it locally:

  ```properties
  # local.properties  (untracked — keep out of git)
  gpr.user=YOUR_GITHUB_USERNAME
  gpr.token=ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxx
  ```
  
  > Alternatively expose `GITHUB_ACTOR` and `GITHUB_TOKEN` as environment variables (CI/CD friendly).
  
  ### 2. Add the Maven repository

  ```kotlin
  // settings.gradle.kts
  dependencyResolutionManagement {
      repositories {  
          google()
          mavenCentral()
          maven {
              name = "PantrixUI"
              url = uri("https://maven.pkg.github.com/developersancho/pantrix-ui-cmp-pckg")
              credentials {
                  username = providers.gradleProperty("gpr.user").orNull
                      ?: System.getenv("GITHUB_ACTOR")
                  password = providers.gradleProperty("gpr.token").orNull
                      ?: System.getenv("GITHUB_TOKEN")
              }
          } 
      }
  }
  ```

  ### 3. Add dependencies

  ```kotlin
  // build.gradle.kts (shared module)
  kotlin {
      sourceSets {
          commonMain.dependencies {
              // Core (required)
              implementation("io.pantrix.ui:core:1.0.0")
              implementation("io.pantrix.ui:components:1.0.0")

              // Icons (pick one or more packs)
              implementation("io.pantrix.icon:core:1.0.0")
              implementation("io.pantrix.icon:lucide:1.0.0")
              implementation("io.pantrix.icon:feather:1.0.0")
              // implementation("io.pantrix.icon:materialsymbols-outlined:1.0.0")
              // ... see full list below
          } 
      }
  }
  ```

  ### 4. Use a component
  
  ```kotlin
  @Composable
  fun App() {
      PantrixTheme(
          config = themeConfig {
              preset = DesignSystemPreset.MATERIAL3
          }
      ) {
          PxButton(   
              text = "Hello PantrixUI",
              onClick = { /* ... */ },
              variant = PxButtonVariant.SOLID,
              color = ComponentColor.PRIMARY,
              size = ComponentSize.MD,
          )
      }
  }
  ```
  
  ---

  ## Available Artifacts

  **Current version**: `1.0.0`
  
  ### UI library (`io.pantrix.ui`)

  | Artifact | Coordinates |
  |----------|-------------|
  | Core (theme engine, tokens, platform utilities, form validation, responsive) | `io.pantrix.ui:core:1.0.0` |
  | Components (65+ UI components) | `io.pantrix.ui:components:1.0.0` |
  
  ### Icons (`io.pantrix.icon`)
  
  | Pack | Coordinates |
  |------|-------------|
  | Core (required by all icon packs) | `io.pantrix.icon:core:1.0.0` |
  | Bootstrap Icons | `io.pantrix.icon:bootstrap:1.0.0` |
  | VS Code Codicons | `io.pantrix.icon:codicons:1.0.0` |
  | Feather Icons | `io.pantrix.icon:feather:1.0.0` |
  | Fluent UI Icons | `io.pantrix.icon:fluent:1.0.0` |
  | Font Awesome | `io.pantrix.icon:fontawesome:1.0.0` |
  | Heroicons | `io.pantrix.icon:heroicons:1.0.0` |
  | Lucide | `io.pantrix.icon:lucide:1.0.0` |
  | Material Icons (legacy) | `io.pantrix.icon:materialicons:1.0.0` |
  | Material Symbols — Core | `io.pantrix.icon:materialsymbols-core:1.0.0` |
  | Material Symbols — Outlined | `io.pantrix.icon:materialsymbols-outlined:1.0.0` |
  | Material Symbols — Outlined Filled | `io.pantrix.icon:materialsymbols-outlinedfilled:1.0.0` |
  | Material Symbols — Rounded | `io.pantrix.icon:materialsymbols-rounded:1.0.0` |
  | Material Symbols — Rounded Filled | `io.pantrix.icon:materialsymbols-roundedfilled:1.0.0` |
  | Material Symbols — Sharp | `io.pantrix.icon:materialsymbols-sharp:1.0.0` |
  | Material Symbols — Sharp Filled | `io.pantrix.icon:materialsymbols-sharpfilled:1.0.0` |
  | Radix Icons | `io.pantrix.icon:radix:1.0.0` |
  | Tabler Icons | `io.pantrix.icon:tabler:1.0.0` |
  
  ### Platform publications
  
  Each artifact publishes the full KMP target matrix: `kotlinMultiplatform`, `android`, `desktop` (JVM), `iosArm64`, `iosSimulatorArm64`, `js`, `wasmJs`. Gradle
  resolves the correct variant for your target automatically.

  ---

  ## Version Catalog (recommended)
  
  ```toml
  # gradle/libs.versions.toml
  [versions]
  pantrix-ui = "1.0.0"
  pantrix-icons = "1.0.0"

  [libraries]
  pantrix-core = { module = "io.pantrix.ui:core", version.ref = "pantrix-ui" }
  pantrix-components = { module = "io.pantrix.ui:components", version.ref = "pantrix-ui" }
  pantrix-icons-core = { module = "io.pantrix.icon:core", version.ref = "pantrix-icons" }
  pantrix-icons-lucide = { module = "io.pantrix.icon:lucide", version.ref = "pantrix-icons" }
  pantrix-icons-feather = { module = "io.pantrix.icon:feather", version.ref = "pantrix-icons" }
  ```

  // build.gradle.kts
  dependencies {
      implementation(libs.pantrix.core)
      implementation(libs.pantrix.components)
      implementation(libs.pantrix.icons.core)
      implementation(libs.pantrix.icons.lucide)
  }
  ```

  ---

  ## Supported Platforms

  | Platform | Minimum |
  |----------|---------|
  | Android | API 24 (compileSdk 36) |
  | iOS | iOS 14+ (Arm64 device + Simulator) |
  | Desktop | JVM 17 |
  | Web | JS (browser), WebAssembly |

  **Tooling**: Kotlin 2.3.20, Compose Multiplatform 1.10.3, AGP 9.1.0, Gradle 9.4.1.
  
  ---

  ## Troubleshooting

  ### `401 Unauthorized` when resolving dependencies
  Your `gpr.token` is missing, expired, or lacks the `read:packages` scope. Re-generate the PAT and update `local.properties`.

  ### `Could not find io.pantrix.ui:core:1.0.0`
  The Maven repository block is missing or pointing to the wrong URL. Confirm `settings.gradle.kts` includes
  `https://maven.pkg.github.com/developersancho/pantrix-ui-cmp-pckg` and the credentials block resolves a real token.
  
  ### Gradle resolves Android variant on a non-Android target
  Make sure you're declaring dependencies inside the correct source set (`commonMain` for shared code, `androidMain` for Android-only).

  ---

  ## Documentation & Resources

  | Resource | Where |
  |----------|-------|
  | Full documentation site | https://pantrixui.com/ |
  | Source code | https://github.com/developersancho/PantrixUI |
  | Issue tracker | https://github.com/developersancho/PantrixUI/issues |
  | Component API reference | [`COMPONENTS.md`](https://github.com/developersancho/PantrixUI/blob/main/COMPONENTS.md) |
  | Design system specification | [`DESIGN_SYSTEM.md`](https://github.com/developersancho/PantrixUI/blob/main/DESIGN_SYSTEM.md) |
  | Release notes | [`CHANGELOG.md`](https://github.com/developersancho/PantrixUI/blob/main/CHANGELOG.md) |
  | Roadmap | [`ROADMAP.md`](https://github.com/developersancho/PantrixUI/blob/main/ROADMAP.md) |

  ---

  ## License

  PantrixUI is licensed under the **Apache License 2.0**. See [LICENSE](https://github.com/developersancho/PantrixUI/blob/main/LICENSE) in the source repository.
  
  ```
  Copyright 2024-2026 Developer Sancho

  Licensed under the Apache License, Version 2.0 (the "License");
  you may not use this file except in compliance with the License.
  You may obtain a copy of the License at
  
      https://www.apache.org/licenses/LICENSE-2.0
  ```

