# 🛠️ PuterVision Pentad: 68-Tool Model Context Protocol Reference

This document provides a comprehensive operational catalog of the **68 specialized Model Context Protocol (MCP) tools** provided by the PuterVision Cognitive Pentad.

---

## 📑 Quick Navigation

- [1. `state-memory-mcp` (13 Tools) — Workflow State Memory](#1-state-memory-mcp-13-tools)
- [2. `vision-memory-mcp` (15 Tools) — Visual Perception & Grounding](#2-vision-memory-mcp-15-tools)
- [3. `world-model-mcp` (15 Tools) — 3D/2D Spatial World Model](#3-world-model-mcp-15-tools)
- [4. `agent-reasoning-mcp` (15 Tools) — Strategic BDI & System 1 Fast Decision Layer](#4-agent-reasoning-mcp-15-tools)
- [5. `behavior-mcp` (10 Tools) — ~60Hz Behavior Tree Execution Engine](#5-behavior-mcp-10-tools)

---

## 1. `state-memory-mcp` (13 Tools)

**Package**: `@putervision/state-memory-mcp` | **Version**: `1.3.0` | **Focus**: Persistent Workflow State Memory

| Tool | Action Modes | Description |
| :--- | :--- | :--- |
| `manage_nodes` | `create`, `update`, `get`, `delete`, `batch_create`, `batch_update`, `add_note` | CRUD operations for workflow entities: tasks, decisions, artifacts, plans, milestones, blockers, observations, and requirements. |
| `manage_edges` | `create`, `delete`, `query`, `link_visual` | Builds and queries directed typed dependency graphs (`depends_on`, `blocks`, `produces`, `references`, `renders_state`). |
| `manage_sessions` | `start`, `end`, `list`, `get` | Multi-turn agent attribution, tracking mutations, active task scopes, and session lifecycle boundaries. |
| `manage_tasks` | `next`, `complete`, `block`, `unblock`, `find_blockers`, `list` | Priority queue execution, topological runnable task extraction, and blocker resolution DAG traversals. |
| `manage_snapshots` | `save`, `restore`, `diff`, `list`, `undo` | Transactional workspace state checkpoints, rollbacks, and structural graph diffing. |
| `manage_specs` | `register`, `verify`, `list`, `get` | State-driven design (SDD) contract baseline registration and automated compliance verification. |
| `manage_database` | `stats`, `audit`, `doctor`, `optimize` | SQLite database maintenance, integrity checks, index tuning, and cryptographic SHA-256 Merkle audits. |
| `manage_data` | `export`, `import`, `export_joint_trajectories`, `export_synergy_metrics` | Interleaved multimodal trajectory extraction connecting workflow steps to visual states and fast decision hashes. |
| `query_graph` | `trace`, `ancestors`, `descendants`, `cycles`, `compact_slice` | Depth-bounded DAG traversal, cycle anomaly detection, and compact `TaskSlice` generation for System 1. |
| `get_analytics` | `summary`, `velocity`, `blockers`, `burndown` | Project health metrics, completion velocity, node distributions, and critical blocker path analysis. |
| `get_events` | `feed`, `changelog`, `replay` | Append-only event-sourced audit log querying with session and timestamp filtering. |
| `run_diagnostics` | `validate`, `repair`, `clean` | Automated graph anomaly detection: cycles, broken pointers, orphaned nodes, and invalid edge relations. |
| `use_blackboard` | `get`, `set`, `delete`, `lease`, `list` | Shared cross-agent memory scratchpad with lease duration TTLs for multi-agent synchronization. |

---

## 2. `vision-memory-mcp` (15 Tools)

**Package**: `@putervision/vision-memory-mcp` | **Version**: `1.3.0` | **Focus**: Perceptual Visual Memory & AX Grounding

| Tool | Action Modes | Description |
| :--- | :--- | :--- |
| `analyze_screenshot` | Single or batch ingestion | Computes perceptual hashes (dHash/pHash), LanceDB vector embeddings, and AX tree element grounding. |
| `recall_memory` | Text query or image similarity | Searches historical visual states via semantic text descriptions or base64 image similarity. |
| `record_outcome` | `transition`, `blocker`, `mutation` | Tracks UI state transitions triggered by actions, constructing empirical navigation graphs. |
| `get_navigation_paths` | BFS path query | Finds deterministic shortest-path UI action sequences to navigate from state $A$ to target state $B$. |
| `predict_next_action` | Action recommendation | Predicts optimal next UI interaction (click, type, scroll) and exact target screen coordinates. |
| `compare_states` | Perceptual or structural diff | Computes perceptual pixel difference, layout shifts, or compares video recordings (`video_a` vs `video_b`). |
| `get_session_context` | `summary`, `compact_slice` | Retrieves visual session history, cache hit metrics, token savings, and sub-1KB `compact_slice` payloads. |
| `manage_snapshot` | `save`, `restore`, `diff`, `export` | Visual memory checkpoints, layout baseline retention, and regression detection snapshots. |
| `manage_visual_spec` | `set`, `verify`, `list` | Visual SDD design contract baseline registration and automated layout regression testing. |
| `manage_video` | `ingest`, `search`, `timeline` | Ingests video recordings, performs semantic search, and extracts timestamped keyframes. |
| `create_evidence_pack` | Multi-modal bundle | Generates cryptographic packages linking video keyframes, state graph tasks, and visual screenshots. |
| `export_trajectories` | `json`, `llava`, `qwen2_vl`, `joint` | Exports multimodal visual fine-tuning datasets and interleaved Pentad agent trajectories. |
| `undo_visual_mutation` | Revert | Rolls back accidental visual state creations or transition edge ingestions. |
| `forget_state` | Purge | Permanently deletes a specific visual state and vector embedding for privacy compliance. |
| `wait_for_visual_state` | Polling barrier | Blocks until a target UI state or element selector becomes visible, or times out. |

---

## 3. `world-model-mcp` (15 Tools)

**Package**: `@putervision/world-model-mcp` | **Version**: `0.5.0` | **Focus**: 3D/2D Spatial Memory & Object Permanence

| Tool | Action Modes | Description |
| :--- | :--- | :--- |
| `update_entity` | `create`, `update`, `patch` | Creates/updates 3D/2D entities with coordinates, AABB bounding boxes, confidence, and custom properties. |
| `query_entities` | FTS5, proximity, tags | Spatial proximity queries (radius search), keyword filtering, status filters, and entity history lookup. |
| `set_relation` | `link`, `update`, `remove` | Registers spatial and topological relationships (`on`, `inside`, `next_to`, `above`, `near`, `contains`). |
| `get_spatial_map` | `json`, `geojson`, `gltf`, `obj`, `summary`, `compact_slice` | Exports structured 3D spatial models, topological graphs, glTF scenes, or $K \le 16$ nearest entity slices. |
| `simulate_movement` | `predict`, `navigate`, `waypoints` | Tests AABB obstacle collisions, simulates velocity/displacement paths, and computes waypoint vectors. |
| `ingest_observation` | Perception merge | Reconciles vision detections into the world model; re-identifies persistent entities and updates poses. |
| `get_expected_view` | Frustum cone calculation | Calculates which entities are visible from an observer position, orientation angles, and FOV cone. |
| `link_to_goal` | `link`, `unlink`, `get_context` | Links spatial entities/regions to `state-memory-mcp` task IDs and extracts goal-relevant entity slices. |
| `record_outcome` | Spatial action log | Persists action execution outcomes, movement displacements, and entity state mutations. |
| `manage_spatial_spec` | `register`, `verify`, `list` | Spatial SDD physical contract baseline registration and geometric boundary verification. |
| `create_evidence_pack` | Cryptographic bundle | Generates SHA-256 spatial evidence bundles linking entity geometries and coordinates to tasks. |
| `use_spatial_blackboard`| `publish`, `claim_lock`, `release` | Multi-agent spatial blackboard for publishing spatial intentions and claiming region mutex locks. |
| `manage_snapshot` | `save`, `restore`, `diff`, `undo` | Spatial time-travel management, point-in-time state diffs, and world model checkpoints. |
| `generate_game_inputs` | Playwright & 3D inputs | Generates Playwright mouse/keyboard inputs and performs 3D-to-screen pixel unprojection. |
| `wait_for_spatial_state`| Polling barrier | Blocks execution until an entity reaches specified spatial conditions. |

---

## 4. `agent-reasoning-mcp` (15 Tools)

**Package**: `@putervision/agent-reasoning-mcp` | **Version**: `0.3.0` | **Focus**: Strategic BDI Cognition & System 1 Fast Decision Layer

| Tool | Subsystem | Description |
| :--- | :--- | :--- |
| `set_goal` | Strategic (System 2) | Hierarchical goal DAG management, objective decomposition into subgoals, and priority assignment. |
| `evaluate_situation` | Strategic (System 2) | Multi-attribute expected utility evaluation (\(E[U] = \sum w_i u_i\)) across multi-modal snapshot context. |
| `replan` | Strategic (System 2) | Adaptive goal DAG reconstruction and fallback strategy formulation upon blockers or failures. |
| `assess_risk` | Strategic (System 2) | Quantitative threat calculation, worst-case impact analysis, and probability-weighted risk ratings. |
| `query_knowledge` | Strategic (System 2) | FTS5 semantic search over historical decision traces, tactical rules, and domain heuristics. |
| `set_utility_weights` | Strategic (System 2) | Configures utility profiles (aggression, caution, greed, efficiency, exploration, cooperation). |
| `get_decision_trace` | Strategic (System 2) | Explainable chain-of-thought rationale playback, scoring breakdowns, and latency telemetry. |
| `manage_beliefs` | Strategic (System 2) | Probabilistic belief tracking with exponential confidence decay and category organization. |
| `manage_intentions` | Coordination | Queue, dispatch, track, and resolve behavior directives (wire contract) for `behavior-mcp`. |
| `manage_reasoning_db` | Storage & Audit | Database maintenance, diagnostics, snapshots, and SHA-256 Merkle audit verification. |
| `classify` | Fast Path (System 1) | Ultra-low-latency ($<1\text{ms}$) categorical classification over multi-modal StatePacks. |
| `ask_noul` | Fast Path (System 1) | Evaluates Boolean propositions with Bayesian prior calibration and strict L1 abstain safeguards. |
| `ask_choice` | Fast Path (System 1) | Selects 1 optimal choice from discrete alternatives ($N \le 16$) with probability simplex margins. |
| `ask_score` | Fast Path (System 1) | Continuous scalar rating of entities or plans on bounded intervals with criteria weights. |
| `gate_intention` | Fast Path (System 1) | Pre-dispatch security gate evaluating blast radius and issuing signed HMAC-SHA256 dispatch tokens. |

---

## 5. `behavior-mcp` (10 Tools)

**Package**: `@putervision/behavior-mcp` | **Version**: `0.3.0` | **Focus**: ~60Hz Behavior Tree Execution Engine

| Tool | Action Modes | Description |
| :--- | :--- | :--- |
| `load_behavior` | `load`, `hot-swap` | Injects, initializes, and starts behavior tree execution loops in the target browser or game runtime. |
| `set_parameters` | `set`, `get`, `reset` | Dynamically updates runtime execution parameters and variables on active behavior instances. |
| `get_status` | `current`, `history` | Queries active execution status, current node traversal path, tick counter, duration, and error state. |
| `abort_behavior` | `abort`, `pause`, `resume`, `unstick` | Immediately halts execution, pauses loop, or triggers unstick recovery with input disengagement. |
| `register_trigger` | `register`, `list` | Configures high-priority reactive interrupts with preemption levels and cooldown guards. |
| `replay_recording` | `capture`, `list`, `replay` | Records and replays deterministic frame sequences with adaptive timing synchronization. |
| `get_metrics` | `current`, `history` | Retrieves runtime execution telemetry, tick duration histograms ($<16.6\text{ms}$), and stuck scores. |
| `manage_behaviors` | `register`, `get`, `list`, `synthesize` | CRUD operations for immutable JSON behavior tree definitions with SHA-256 tree hash verification. |
| `manage_blackboard` | `get`, `set`, `delete`, `lease`, `list` | Reads, writes, leases, and inspects shared blackboard state variables (including `semantic_decision_*`). |
| `manage_runtime_db` | `stats`, `audit`, `doctor`, `snapshot` | Database maintenance, health diagnostics, and SHA-256 Merkle audit verification. |

---

## 🔗 Related Documentation

- [**PuterVision Organization README**](https://github.com/putervision/.github/blob/main/profile/README.md)
- [**System One & Jev-Style Architecture Deep Dive (`ARCHITECTURE.md`)**](https://github.com/putervision/.github/blob/main/profile/ARCHITECTURE.md)
- [**Getting Started & Client Configuration Guide (`GETTING_STARTED.md`)**](https://github.com/putervision/.github/blob/main/profile/GETTING_STARTED.md)
