# A useful Minecraft Java mod problem report

A good report lets someone reproduce the same failure without guessing which game, loader, file, or launcher instance you mean. Use this template for a Java Edition mod issue, then send it to the mod's documented support channel. It does not apply to Bedrock Add-Ons or Paper/Spigot plugins.

This is an independent documentation resource from the Universal Modder Field Guide. It is not an official Minecraft, Fabric, Forge, NeoForge, or upstream Universal Modder support form.

## Identify the first failing stage

Choose one stage before describing the error:

| Stage | Useful evidence |
|---|---|
| Building source | The Gradle task, selected JDK, and first relevant build error |
| Starting the development client | Run configuration, development log, and exact source revision |
| Starting an installed mod | Launcher instance, loader version, actual JAR, and instance log |
| Opening a world | Whether the same mod set can open a new test world |
| Using a feature | Exact item, recipe, texture, command, or action that fails |
| Joining a server | Client/server game versions, loaders, and required mod versions |

“The game crashes” and “my item has a missing texture” are different reports. A compile error occurs before there is a finished mod to put in the launcher's `mods` folder.

## Copy and fill this template

Replace every bracketed field. Write `not checked` where you have no observation; do not turn an unrun check into a pass.

```text
Title: [mod name] — [first failing stage] — [short symptom]

What I expected:
[One observable result.]

What actually happened:
[Error screen, crash, missing item, broken recipe, etc.]

Environment:
- Minecraft edition: Java Edition
- Exact Minecraft version:
- Loader name and exact version:
- Mod name, version, and exact JAR filename:
- Mod download/source URL:
- Required dependencies and their versions:
- Launcher and launcher version:
- Active instance/game directory: [redact the private part]
- OS and architecture:
- Java runtime selected by the launcher:
- Client, dedicated server, or both:
- Other installed mods: [names and versions, or a reviewed mod-list link]

For source/build problems only:
- Repository URL and commit/release:
- Gradle wrapper version:
- JDK reported by ./gradlew --version or .\gradlew.bat --version:
- IDE Gradle JVM, if using an IDE:
- Exact task/run configuration that fails:

Steps to reproduce:
1.
2.
3.

Evidence:
- Last relevant change before the failure:
- First relevant exception and its surrounding context:
- Reviewed latest.log or build-output link:
- Reviewed crash-report link, if one was generated:
- Screenshot, if it clarifies the exact symptom:

Checks actually performed:
- Matching loader with no newly added mod: [pass/fail/not checked]
- New mod plus its required dependencies: [pass/fail/not checked]
- Fresh test world in that same setup: [pass/fail/not checked]
- Final release JAR in a separate launcher instance: [pass/fail/not checked]
- Dedicated server, if relevant: [pass/fail/not checked]

One change already tried, and its result:
[Do not omit a failed experiment.]
```

## Find the evidence from the failing run

For an installed mod, open the game directory of the **instance you actually launched**, then find `logs/latest.log`. A crash report, when generated, is under `crash-reports`. Third-party launchers can store instances elsewhere than the official launcher's default directory. [Fabric's log guide](https://docs.fabricmc.net/players/troubleshooting/uploading-logs) explains both the distinction and normal log-sharing options.

For a development client, use the run directory named by your build configuration. Forge and NeoForge MDKs do not necessarily use the same run-directory layout. If Gradle failed before the client opened, attach the build output rather than an unrelated old game log.

For a trusted development workspace, these commands report version information; they are not a fix:

```sh
java -version
javac -version
./gradlew --version
```

In Windows PowerShell, use `java -version`, `javac -version`, and `./gradlew.bat --version` (or `.\gradlew.bat --version`). The terminal's Java, IDE's Gradle JVM, and launcher's game runtime may differ. Report the one that actually failed. [Gradle documents these JVM selection differences](https://docs.gradle.org/current/userguide/gradle_daemon.html).

## Keep the comparison small

Use a separate instance and a test world. Record one reversible change, rerun the same steps, and preserve both outcomes. Keep required dependencies when testing a mod on its own. Do not remove content mods from your valuable original world just to produce a minimal report.

When reporting an installed-JAR problem, identify the actual release file. A `-sources.jar` or `-javadoc.jar` is not the playable mod. A working IDE development client also does not establish that the file you shared loads in a clean launcher instance. [NeoForge's versioned build documentation](https://docs.neoforged.net/docs/1.21.1/gettingstarted/) treats building the artifact and launching the development environment as separate steps.

## Review before sharing

Read a log before posting it publicly. Remove credentials, access tokens, private server addresses, and private path components where they appear. Keep error class names, mod IDs, dependency versions, and enough surrounding context to diagnose the problem. Do not publish a whole world save or a private configuration archive when a log and reproduction steps are enough.

Follow the target support channel's instructions about full logs, paste services, formatting, and screenshots. This template does not grant permission to promote a website in somebody else's support thread.

For explanations behind the fields, see the [independent Minecraft troubleshooting guide](https://universalmodder.dev/guides/minecraft-mod-not-loading/) and its [edition, loader, and Java reference](https://universalmodder.dev/guides/minecraft-mod-loaders/).

## Sources and scope

Reviewed October 12, 2026 against the linked official documentation. This document was prepared with AI assistance and checked against source material. It is a reporting worksheet, not a record of successful installation, compilation, game testing, or compatibility across loaders.

