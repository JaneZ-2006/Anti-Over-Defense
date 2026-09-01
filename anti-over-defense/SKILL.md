---
name: anti-over-defense
description: Directly complete software implementation, feature development, user-requested refactoring, bug fixing, and large coding tasks while preventing unrequested defensive infrastructure, approval processes, speculative fallback paths, unnecessary abstraction, and validation expansion. Use whenever Codex must implement, modify, repair, or finish a software project. Do not use for explicitly requested security reviews, hardening, compliance work, or dedicated testing projects.
---

# Anti Over-Defense

Complete the requested software result directly. Preserve the project's existing shape and add only the code, files, and checks needed for the current task.

## Execute the task

1. Identify the concrete result the user requested.
2. Read the code and instructions directly related to that result.
3. Follow the project's existing implementation, interfaces, structure, and commands.
4. Modify the smallest relevant scope. Interpret "smallest" as no unrelated structure or behavior, not as the fewest lines of code.
5. Reuse existing functions, modules, data structures, and tooling.
6. Run the project's existing directly relevant tests, build commands, or examples.
7. Fix failures caused by the current change. Report unrelated failures without absorbing them into the task.
8. Stop expanding once the requested behavior works and the directly relevant checks pass.
9. Deliver the implementation and summarize the changes and checks concisely.

Do not replace implementation with planning, risk discussion, tables, reports, or recommendations. Plan only to the degree needed to perform the work.

## Apply rules by behavior

Apply every restriction below to the actual purpose and effect of proposed code, files, and process. Do not treat the labels as banned words. Do not evade a restriction by renaming the same behavior: a "readiness check" can still be a gate, "file identity" can still be a digest, and "run history" can still be an audit system.

### Hashes and SHA256

Do not introduce content-identity or integrity infrastructure for ordinary project files, generated artifacts, configuration, intermediate results, or local data. This includes:

- Computing file digests or fingerprints.
- Generating checksum files or digest manifests.
- Using content digests as change detectors, cache keys, or version identifiers.
- Comparing before-and-after hashes.
- Adding provenance or tamper checks to ordinary or one-off output.
- Creating content-addressed storage for local intermediate files.
- Requiring a digest match before completing the task.

Instead, read and write the target paths directly, use the existing project structure, run the relevant existing command, and judge completion from actual program behavior. Preserve an existing digest mechanism when the project already depends on it.

### Smoke checks

Do not create a second, shallow validation layer outside the project's tests. This includes smoke tests, sanity scripts, startup checks, health commands, minimum-run wrappers, quick-validation workflows, one-off test entry points, or wrappers around simple existing commands.

Instead, run the relevant existing unit or integration tests, build command, or example. Do not make a newly invented quick check a delivery prerequisite.

### Release approval

Do not turn completion into a separate approval process. Do not add go/no-go decisions, `approved`, `rejected`, or `ready` states, delivery approvers, release-decision functions, completion controllers, approval checklists, or another confirmation for work the user already authorized.

Instead, deliver when the requested function is implemented and the directly relevant existing checks pass.

### Gates

Do not add a check that must pass before implementation, build, execution, or delivery. This includes quality or validation gates, preflight or readiness checks, commit or runtime checkers, new mandatory CI stages, warning-to-error promotion, check aggregators, or a unified pass interface.

Instead, use the project's current build and test requirements without broadening them. Do not withhold the core result because an unrequested check is absent.

### Contracts

Do not add a formal constraint layer between existing functions, modules, or data. This includes contract classes or tests, design-by-contract frameworks, precondition or postcondition systems, invariant frameworks, assertion wrappers, duplicate internal schemas or types, validation wrappers, formal interaction descriptions, or an interface-guarantee layer for one call.

Instead, follow the existing interface and implement the requested behavior directly. Add only input validation inherently required by the requested behavior or already established by the project.

### Admission

Do not add a mechanism that decides whether an input, component, implementation, environment, or execution method is eligible to participate. This includes allowlists, eligibility checks, capability registries, environment certification, backend or plugin registration, component certification, input-type registration, device support lists, or enablement states.

Instead, call the existing component directly. Use an existing registration mechanism only when the project already requires it.

### Thresholds

Do not invent numeric or status conditions for task completion. This includes minimum coverage, pass rate, performance gain, sample count, score, confidence, or completeness; maximum file size, runtime, error count, or warning count; and any advisory metric promoted to an acceptance condition.

Instead, decide completion from the user's requirements and observed functionality.

### Policies and strategies

Do not turn a direct decision or single implementation into a configurable, replaceable, or composable decision system. This includes policy or strategy classes, Strategy Pattern, rules engines, pluggable selectors, dynamic schedulers, decision tables, configuration-driven behavior, multi-mode execution, backend-selection frameworks, automatic environment selection, or extension interfaces for implementations that do not exist.

Instead, implement the one currently required behavior with a direct condition or function using the project's established style.

### Latency work

Do not introduce timing measurement, limits, or performance acceptance work unless performance is part of the user's task. This includes timers, latency or timeout budgets, performance thresholds, benchmarks, reports, timing logs, duration statistics, proactive tuning, or timeout-and-retry systems for ordinary calls.

Instead, verify functional behavior with existing commands. When the user explicitly requests performance optimization, GPU profiling, or benchmarking, measure only the relevant scope and do not spread performance work elsewhere.

### Blocking

Do not pause or refuse implementation for an issue that does not affect the core result. Non-blockers include unresolved internal naming, minor presentation choices, several similar internal implementations, unrelated test failures, missing optional tools, inability to test every environment, theoretical risks, or details reasonably inferable from the code.

Instead, make a reasonable local choice and continue. Ask only when missing information would materially change user-visible behavior, a public interface, data, an irreversible action, an external system call, or required permissions.

### Security boundaries

Do not invent permission, isolation, or trust architecture for an ordinary local engineering task. This includes sandbox wrappers, permission layers, trust zones, execution isolation, access-control modules, permission proxies, capability tokens, trusted/untrusted module partitions, file-operation permission validators, or authorization checks around local function calls.

Instead, obey the environment's real permission model and user authorization. Do not introduce a new security model for theoretical risk.

### Auditing

Do not add a history or evidence-retention system for the current feature. This includes audit logs, operation-history databases, change tables, event trails, evidence files, archived run reports, per-step records, dedicated trace IDs, function-call history, process reports, or a new logging channel created to prove completion.

Instead, use the project's existing logging system for operationally necessary information and report the final result in the response. Do not save intermediate evidence merely to demonstrate that work occurred.

### Tightening

Do not make the system stricter than the user requested or the project currently behaves. Do not reject previously accepted inputs, narrow support, add required fields, enforce stricter formats or types, convert warnings into errors, change permissive parsing to rejection, narrow permissions, add state restrictions, or alter defaults so more cases fail.

Instead, preserve compatibility and fix the current issue. Change the acceptance range only when the user explicitly requests it or the existing specification requires it.

### Real-environment testing

Do not make full real-world validation a prerequisite for implementation or delivery. Do not require every target device, real hardware, complete production data, all operating systems or dependency versions, a full benchmark, or the entire test matrix when directly relevant checks are sufficient.

Instead, perform the relevant validation available in the current environment and state precisely what could not be run. Do not invalidate completed code solely because exhaustive testing is unavailable.

### Branches

Do not add implementation paths for situations that have not occurred. This includes speculative conditions, compatibility or legacy paths, backup implementations, special-environment paths, automatic downgrade paths, parallel old and new implementations, empty future backends, many edge-case branches, unnecessary Git branches, unnecessary worktrees, or multiple development routes for one direct change.

Instead, implement the current path. Add only conditions required by actual current inputs and behavior.

### Legality frameworks

Do not build a general rules layer to decide whether an input, state, component, or operation is allowed. This includes legality checkers, validity frameworks, allowed-state tables, eligibility classifiers, duplicate validation, complete transition-rule systems, or a generic decision module around a simple condition.

Instead, retain or add only the basic check needed by the current function, using the project's existing conventions.

### Protocols

Do not turn a simple module interaction into a formal communication or state-transition system. This includes handshakes, version negotiation, message envelopes, sequence numbers, state machines, multi-stage confirmation, custom message formats, capability negotiation, request/response object systems for local calls, or start-confirm-complete states around a simple operation.

Instead, use direct function calls, existing data structures, and existing interfaces.

### Detours

Do not avoid the direct cause of a failure by adding another processing route. This includes workarounds, bypasses, fallbacks, secondary paths, automatic downgrade, silent continuation after errors, skipping failed components, copied temporary implementations, direct internal-state access that evades an interface, or a special route for the current error.

Instead, fix the direct cause in the existing path. Propagate or report real errors according to current project behavior rather than hiding them.

### Consistency systems

Do not add synchronization, comparison, or automatic-repair infrastructure across files, objects, caches, or components. This includes consistency checkers, reconciliation, state balancing, dual-write verification, cache/source comparison, replica synchronization, repair jobs, transaction coordinators, cross-module invariant checks, duplicate-data validation, or before-and-after state comparison for local edits.

Instead, keep one source of truth where possible and update the data required by the current function directly.

## Prevent adjacent expansion

Do not:

- Write handling for a problem that has not occurred.
- Create future extension points, plugin systems for one implementation, or configuration for fixed behavior.
- Turn a local change into a general framework.
- Wrap simple data in multiple layers or create multiple manager classes for one function.
- Add internal states or long-lived infrastructure for a one-time task.
- Create proof artifacts, recovery systems for simple errors, or several unrequested solutions.
- Refactor unrelated modules, unify the entire code style, or absorb historical issues.
- Continue adding defensive code after the requested function is complete.
- Rename any prohibited behavior and implement its semantic equivalent.

Prefer existing files over new files, direct calls over indirection, one current implementation over extensibility, and actual output over proxy evidence.

## Handle uncertainty

Infer a reasonable choice and continue when alternatives do not materially change:

- User-visible behavior.
- Public interfaces.
- Data content.
- Irreversible operations.
- External system calls.
- Permission requirements.

Do not stop for private names, local function organization, minor presentation details, implementation patterns evident in nearby code, easily changed defaults, or internal choices that do not affect the interface.

Ask the user when the missing choice would materially change the final result or introduce a new external side effect. Follow higher-priority instructions that require approval rather than treating this skill as authorization.

## Verify directly

Run existing relevant tests, builds, and examples. Check that the modified behavior works and fix failures introduced by the change.

Do not create a validation system, delivery checker, completion decision flow, device matrix, performance metric, coverage target, repeated check that yields no new information, or evidence file. Do not let an unrelated failure prevent delivery of the completed core task; report it accurately.

Never fabricate a passing result or hide an error. If a relevant command cannot run, state why and distinguish unverified behavior from failure.

## Apply necessary exceptions narrowly

Obey system permissions, repository instructions, user authorization, and existing public interfaces. Do not leak credentials, ignore a concrete data-corruption risk, delete a required existing mechanism, or perform an unauthorized external action.

Introduce an otherwise restricted behavior only when at least one of these conditions is true:

1. The user explicitly requests it.
2. The repository's existing instructions explicitly require it.
3. The current build or test flow already depends on it.
4. A concrete error that has already occurred cannot be solved more directly.
5. Omitting it would immediately cause clear data loss, an unauthorized external operation, or irreversible damage.

Implement only the smallest part needed for the concrete exception. Do not use the exception to build a general system. Future usefulness, completeness, caution, or abstract engineering quality alone do not qualify.

## Finish

Deliver immediately when:

- The requested core behavior is implemented.
- The change fits the existing project.
- The relevant code builds or runs.
- Existing directly relevant tests pass, when available.
- No known error was introduced by the change.

After these conditions hold, do not add protection, extensibility, helper infrastructure, unrelated optimization, unrelated refactoring, a future-work checklist, or recommendations for new project-wide systems.
