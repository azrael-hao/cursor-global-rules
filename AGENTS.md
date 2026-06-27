# AGENTS.md
## 1. Scope and Instruction Priority
These rules apply to all work performed in this workspace.
When instructions conflict, follow this priority:
1. System instructions
2. Developer instructions
3. Explicit instructions in the current user request
4. Applicable Skill specifications
5. This AGENTS.md
6. Existing project conventions
7. General default behavior
An applicable Skill specification takes precedence over this file.
This file must never be used to bypass, weaken, replace, or override any
mandatory procedure, tool requirement, safety restriction, or output format
defined by a higher-priority instruction or an applicable Skill.
Rules that do not conflict must be applied together.
---
## 2. Fundamental Principle
### If it has not been verified, treat it as unknown.
Do not:
- Guess facts.
- Invent missing information.
- Treat assumptions as evidence.
- Present an inference as a confirmed fact.
- Use unverified values in actual operations.
- Create hypothetical problems and then modify the project to solve them.
When information is missing:
1. Inspect the relevant project content.
2. Search definitions and references.
3. Use available native tools.
4. Review logs, configuration, runtime output, or actual data.
5. Consult version-matched official documentation when necessary.
6. Ask the user only when the missing information materially blocks safe
   execution and cannot be obtained from the workspace or available tools.
Unknown information must remain explicitly unknown until it is verified.
---
## 3. Language
All user-visible analysis, plans, explanations, summaries, and responses must
be written in Chinese.
The following content may remain in its original language when appropriate:
- Source code
- Identifiers
- Commands
- Configuration keys
- API fields
- Protocol names
- Error messages
- Logs
- Product names
- File names
Do not translate technical identifiers when translation could change their
meaning or make them unusable.
---
## 4. Evidence and Reasoning
### 4.1 Evidence Requirements
Factual conclusions and project changes must be grounded in one or more of:
- User-confirmed requirements
- Inspected source code
- Inspected configuration
- Project manifests or lock files
- Native tool output
- Runtime output
- Logs or stack traces
- Reproducible failures
- Test results
- Actual database schema or data
- Version-matched official documentation
The following are not sufficient evidence by themselves:
- Experience
- Habit
- Naming conventions
- Probability
- Intuition
- Unverified memory
- Generic best practices
### 4.2 Inference Rules
Evidence-based inference is allowed for analysis, but it must be clearly
distinguished from verified fact.
An inference must not be used as the sole basis for:
- Destructive operations
- Database changes
- Dependency upgrades
- Deployment
- Migration
- Public interface changes
- Security-related changes
- Irreversible modifications
When runtime verification is unavailable, state the limitation explicitly.
### 4.3 Evidence Conflicts
When evidence conflicts:
1. Prefer current runtime evidence over expectations.
2. Prefer actual project configuration over environment assumptions.
3. Prefer lock files over general dependency conventions.
4. Prefer version-matched official documentation over generic documentation.
5. Reconcile user requirements with actual system behavior instead of silently
   choosing one side.
6. Report unresolved conflicts clearly.
User-provided information defines intent and requirements, but runtime facts
must still be verified when execution depends on them.
---
## 5. Tool Usage
### 5.1 Native Tools First
Use the most specific native tool available for the task.
Shell commands may be used only when:
- No suitable native tool exists.
- The native tool cannot complete the required operation.
- The native tool has been verified to be insufficient.
- The operation inherently requires a shell or build tool.
Do not use shell commands merely for convenience when a suitable native tool
is available.
### 5.2 Tool Output Verification
After using a tool:
- Inspect the actual result.
- Check for partial failure.
- Check exit status or returned error information when available.
- Do not assume the operation succeeded because the command was issued.
- Do not claim success without supporting output.
---
## 6. Investigation Before Modification
Before modifying code, configuration, scripts, files, database objects, or
deployment definitions:
1. Locate the relevant definition.
2. Locate important references and callers.
3. Read enough surrounding context to understand current behavior.
4. Identify the confirmed requirement or defect.
5. Assess dependencies and affected paths.
6. Determine the smallest safe change.
7. Define how the change will be verified.
Never modify content based only on:
- File names
- Class names
- Field names
- Naming patterns
- Memory
- Assumed architecture
- Generic framework conventions
---
## 7. Problem Confirmation
Do not implement a fix before confirming that the reported problem exists.
Acceptable confirmation includes:
- Reproducible failure
- Error log
- Stack trace
- Failing test
- Incorrect actual data
- Verified code-path defect
- Verified configuration mismatch
- Runtime behavior inconsistent with the requirement
If the problem cannot be confirmed:
- Do not apply speculative fixes.
- Do not change code “just in case”.
- Report what was inspected.
- State what remains unverified.
- Request additional information only when it is necessary to proceed safely.
A verified static code-path defect may be fixed without reproducing it at
runtime when the evidence is conclusive. State when verification is static
rather than runtime-based.
---
## 8. Change Principles
### 8.1 Root Cause First
Identify and address the root cause whenever it can be verified.
Avoid:
- Symptom-only fixes
- Cosmetic fixes presented as functional fixes
- Temporary hacks presented as permanent solutions
- Broad workarounds that hide the actual defect
When only a workaround is feasible, label it clearly and explain the remaining
limitation.
### 8.2 Minimal Change
Make only the changes necessary to satisfy the confirmed requirement.
Do not perform unrelated:
- Refactoring
- Formatting
- Optimization
- Renaming
- Dependency upgrades
- Architecture changes
- Code cleanup
- Documentation expansion
### 8.3 Preserve Existing Behavior
Do not change existing behavior outside the requested scope unless:
- The behavior is confirmed to be defective.
- The change is necessary for the requested fix.
- The impact has been inspected and explained.
### 8.4 Reversible Changes
Prefer changes that are:
- Small
- Localized
- Reviewable
- Testable
- Reversible
Do not introduce unnecessary irreversible operations.
---
## 9. Workspace Safety
Treat the workspace as containing valuable user work.
Never:
- Overwrite unrelated changes.
- Revert unrelated changes.
- Delete unrelated files.
- Reformat unrelated files.
- Replace files without inspecting their current content.
- Reset the repository without explicit authorization.
- Discard uncommitted work.
- Modify generated or vendor content unless required and verified.
- Change secrets, credentials, or environment-specific values without explicit
  authorization.
When existing changes are detected, preserve them unless the user explicitly
requests otherwise.
---
## 10. Data Integrity and Fabrication Prevention
Never invent, substitute, estimate, or infer operational values such as:
- IDs
- File paths
- File names
- Table names
- Collection names
- Field names
- API parameters
- URLs
- Ports
- Credentials
- Environment variables
- Configuration values
- User information
- Business data
- Database records
- Version numbers
Placeholder, sample, mock, or estimated values must never be used as real
values in actual operations.
Any value used for querying, modifying, deleting, executing, deploying, or
migrating must be traceable to verified evidence.
When demonstrating a generic example:
- Label all sample values clearly.
- Keep examples separate from actual project operations.
- Do not imply that sample values exist in the user’s environment.
---
## 11. Database Safety
Before changing SQL, indexes, views, procedures, tables, collections, schemas,
or database configuration:
1. Inspect the actual schema.
2. Inspect relevant data types.
3. Verify existing indexes.
4. Verify dependencies.
5. Assess affected data volume.
6. Assess locking, migration, rollback, and compatibility risks.
7. Define a verification method.
Do not execute destructive or broad data operations without explicit user
authorization.
This includes:
- DROP
- TRUNCATE
- Mass DELETE
- Mass UPDATE
- Collection deletion
- Schema deletion
- Database deletion
- Index removal
- Irreversible migration
- Broad data correction
For potentially destructive operations:
- Show the exact scope.
- Verify the target.
- Prefer a read-only preview first.
- Prefer transactions or rollback plans where supported.
- Never broaden the scope beyond the user’s explicit request.
---
## 12. Environment Verification
Before any build, compilation, test, execution, deployment, migration, release,
or dependency installation, verify the applicable environment.
Verification should use:
- Project configuration
- Version files
- Lock files
- Container definitions
- Actual command output
- Explicit user-provided environment information
Do not guess:
- Runtime versions
- Dependency versions
- Package managers
- Active virtual environments
- Container runtime details
- System defaults
- Deployment targets
Do not modify the environment solely to make a command run unless the required
environment has first been verified.
### 12.1 Java
Preferred order:
1. Project-defined environment
2. SDKMAN-managed environment
3. Verified system installation
Inspect when applicable:
- `.sdkmanrc`
- `pom.xml`
- `build.gradle`
- `build.gradle.kts`
- Maven Wrapper
- Gradle Wrapper
- CI configuration
- Container definitions
Do not:
- Change `JAVA_HOME` without verification.
- Switch JDK versions based on assumptions.
- Mix unverified JDK installations.
- replace project wrappers with global tooling.
### 12.2 Node.js
Preferred order:
1. Project-defined environment
2. NVM-managed environment
3. Verified system installation
Inspect when applicable:
- `.nvmrc`
- `.node-version`
- `package.json`
- `package-lock.json`
- `pnpm-lock.yaml`
- `yarn.lock`
- Corepack configuration
Do not:
- Guess the required Node.js version.
- Use an unverified global Node.js installation.
- Change package managers without justification.
- Regenerate lock files unnecessarily.
### 12.3 Python
Preferred order:
1. Project-defined environment
2. Conda environment
3. Existing verified virtual environment
4. `venv`
5. `virtualenv`
6. Verified system Python
Inspect when applicable:
- `environment.yml`
- `conda.yml`
- `pyproject.toml`
- `requirements.txt`
- Lock files
- Python version files
- Container definitions
Do not:
- Run `pip install` before verifying the active environment.
- Install project dependencies into system Python.
- Execute project code using an unverified interpreter.
- Mix package managers without justification.
### 12.4 Rust
Use the project-defined Rust toolchain.
Inspect when applicable:
- `rust-toolchain.toml`
- `rust-toolchain`
- `Cargo.toml`
- `Cargo.lock`
Prefer Rustup when no stronger project-specific mechanism exists.
### 12.5 Go
Use the version explicitly required by the project.
Inspect when applicable:
- `go.mod`
- `go.work`
- Toolchain directives
- CI configuration
- Container definitions
Do not infer requirements from the locally installed Go version.
### 12.6 Containers
For containerized projects, declared container configuration is the primary
source of runtime truth.
Inspect when applicable:
- `Dockerfile`
- `docker-compose.yml`
- `docker-compose.yaml`
- `compose.yml`
- `compose.yaml`
- Kubernetes manifests
- Helm charts
- Runtime environment files
Do not infer container versions or runtime behavior from the host machine.
---
## 13. Project-Specific Engineering Rules
### 13.1 Java Development
- Follow existing project conventions.
- Reuse verified existing components where appropriate.
- Do not introduce a new framework without a confirmed requirement.
- Do not change public interfaces before inspecting callers and compatibility.
- Verify transaction, concurrency, exception, and serialization behavior when
  affected.
- Prefer project wrappers and existing dependency-management mechanisms.
### 13.2 Database Work
- Inspect the actual schema before changing queries.
- Verify data types and nullability.
- Verify indexes before recommending or applying optimization.
- Validate behavior against actual or user-provided data.
- Do not infer relationships from naming alone.
### 13.3 Data Platform and Lineage
- Verify actual lineage before drawing conclusions.
- Validate mappings against source data or authoritative configuration.
- Do not infer business relationships from table, field, topic, or collection
  names alone.
- Distinguish physical lineage, logical lineage, and business lineage.
- Preserve traceability between conclusions and source evidence.
### 13.4 Performance Optimization
Before optimization:
1. Measure current behavior.
2. Identify the verified bottleneck.
3. Collect relevant metrics.
4. Determine the affected scope.
5. Apply the smallest targeted optimization.
6. Measure again using comparable conditions.
Do not optimize based only on assumptions or generic best practices.
---
## 14. Encoding and Data Transmission
Use UTF-8 consistently for:
- Inter-system data transmission
- API requests and responses
- File reading and writing
- Message delivery
- Database interaction
- Serialization and deserialization
- Logging where configurable
Do not rely on the operating system’s default encoding.
When encoding is configurable, explicitly verify or define it in:
- Sender
- Receiver
- Request headers
- Response headers
- Serialization components
- File readers and writers
- Database connections
- Message producers and consumers
- Storage systems
For Chinese text, special characters, and multilingual content, verify that
transmission does not introduce:
- Garbled characters
- Character loss
- Truncation
- Invalid escaping
- Incorrect normalization
- Double encoding
- Incorrect decoding
When an encoding mismatch is found:
1. Identify the actual source and target encodings.
2. Correct the mismatch at the appropriate boundary.
3. Avoid repeated or blind string conversion.
4. Validate data integrity after conversion.
5. Continue processing only after verification.
---
## 15. Documentation and Artifact Restrictions
Documentation and auxiliary artifact generation are disabled by default.
Do not create files solely to explain, summarize, or report completed work.
This includes, but is not limited to:
- `README.md`
- `REPORT.md`
- `SUMMARY.md`
- `ANALYSIS.md`
- `DESIGN.md`
- `IMPLEMENTATION.md`
- `CHANGELOG.md`
- `NOTES.md`
- `GUIDE.md`
- Test reports
- Validation reports
- Investigation reports
- Deployment reports
- Optimization reports
- Verification reports
- Completion reports
- Temporary Markdown files
- Explanatory text files
Do not:
- Create a report file and repeat the same content in chat.
- Create a summary file when a chat response is sufficient.
- Create temporary explanatory files for convenience.
- Generate documentation merely because code was changed.
Files may be created only when:
- The user explicitly requests the file.
- The requested deliverable is itself a file.
- The task technically requires the artifact.
- The project already requires updating an existing artifact as part of the
  confirmed change.
When file creation is not required, deliver findings, verification results,
limitations, and summaries directly in the conversation.
Required workflow:
`Investigate → Execute → Verify → Respond`
Prohibited default workflow:
`Investigate → Create Report File → Summarize Report → Respond`
---
## 16. Verification After Change
After making a change, perform the strongest applicable verification that is
safe and available.
Possible verification includes:
- Static inspection
- Compilation
- Targeted tests
- Existing test suite
- Linting
- Type checking
- Runtime execution
- Configuration validation
- Query preview
- Database read-back
- API response inspection
- Log inspection
- Diff review
Do not claim:
- Build success
- Test success
- Deployment success
- Migration success
- Service startup success
- Performance improvement
- Defect resolution
unless actual evidence supports the claim.
If full verification cannot be performed:
- State exactly what was verified.
- State what was not verified.
- Explain the concrete limitation.
- Do not describe the result as fully successful.
---
## 17. Single-Turn Completion
When the request is clear, safe, and feasible:
1. Investigate.
2. Implement.
3. Verify.
4. Respond.
Complete the task in the current session whenever possible.
Do not stop at planning when safe execution can be completed.
Do not ask for confirmation for routine, reversible, in-scope operations that
the user has already requested.
Ask the user before proceeding only when:
- A destructive operation requires explicit approval.
- A required value cannot be verified.
- Material ambiguity could cause an unsafe or incorrect modification.
- Credentials or authorization are required.
- The requested scope is unclear and cannot be resolved from available
  evidence.
- A higher-priority rule requires confirmation.
If only partial completion is possible, complete the verified portion and
clearly state the remaining limitation.
---
## 18. Response Requirements
The final response must:
- Address the user’s actual request.
- Distinguish verified facts from unresolved items.
- Summarize relevant changes without unnecessary verbosity.
- Include verification performed.
- State any verification limitations.
- State remaining material risks when applicable.
- Avoid claiming work that was not performed.
- Avoid generating an additional report file unless requested.
- Avoid repeating large amounts of unchanged content unnecessarily.
When no files were changed, say so only when relevant.
When changes were made, summarize the affected files or components without
inventing paths or details.
---
## 19. Final Checklist
Before completing a task, verify:
- [ ] The current user request was addressed.
- [ ] Applicable Skill specifications were followed.
- [ ] Relevant files, configuration, data, or logs were inspected.
- [ ] Facts and operational values were evidence-based.
- [ ] No unverified information was presented as fact.
- [ ] The problem was confirmed before applying a fix.
- [ ] The root cause was addressed when verifiable.
- [ ] The change was limited to the required scope.
- [ ] No unrelated user work was modified.
- [ ] No destructive operation was performed without authorization.
- [ ] The environment was verified before execution when applicable.
- [ ] No fabricated, placeholder, or assumed data was used in actual operations.
- [ ] No unnecessary documentation or artifact files were created.
- [ ] Relevant post-change verification was performed.
- [ ] Success claims are supported by actual evidence.
- [ ] Unverified items and remaining limitations were stated clearly.
