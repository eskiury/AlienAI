# Alien: Isolation AI Architecture inside Unreal Engine 5

<p align="center">
  <img src="https://img.shields.io/badge/Unreal%20Engine-5.x-blue.svg?style=for-the-badge&logo=unrealengine" alt="Unreal Engine 5">
  <img src="https://img.shields.io/badge/C%2B%2B-Native-orange.svg?style=for-the-badge&logo=c%2B%2B" alt="Native C++">
  <img src="https://img.shields.io/badge/Architecture-State%20Trees%20%26%20Director-red.svg?style=for-the-badge" alt="AI Architecture">
</p>

## 🕹️ Overview
This project is a high-performance **systemic AI testing ground developed in Unreal Engine 5**, replicating the dual-layer stalking mechanics of *Alien: Isolation*. Moving away from rigid state structures, the architecture leverages native **C++ subsystems** combined with the new **UE5 State Trees** framework to manage dynamic environmental tension and non-deterministic hunting behaviors in real-time.

---

## 📽️ System Demonstration & Media

---

## 🧠 Architectural Highlights

### 1. Dual-Level AI Framework (The Systemic Loop)
The AI is completely decoupled into two independent systemic layers to maintain organic pacing:
*   **The Director Agent (Omniscient C++ Class):** Tracks world states, lever mechanics, and player pressure parameters. It doesn't instantly reveal locations, but mathematically updates a `fCurrentTension` threat meter to dispatch spatial hints or trigger systemic cooldowns.
*   **The Actuating Agent (Xenomorph Character):** Operates as a organic biological hunter. It navigates dynamically over the `NavMesh` via multi-profile stimuli lookups, switching weights dynamically based on short-term memory traces.

### 2. Custom Volumetric Vision System (Native C++)
Instead of using basic 2D perception cones that cause rendering line discrepancies across varying heights, I implemented a custom tridimensional **Skeletal-Bound Multi-Zone Vision Sensor** from scratch using optimized C++ queries:
*   **Bone-Attached Senses:** The vision cones are directly attached to the skeletal head bone rather than the rigid capsule component. This means if an animation shifts the model's head to look sideways, the line traces dynamically rotate with it.
*   **Multizone Evaluation Matrix:** Features 4 distinct volumetric zones (Focal, Far-Range, Peripheral, and Flank support) operating with customizable fill rates mapped via **Data Assets**.

### 3. State Tree Superiority over Behavior Trees
Leveraging **Unreal Engine 5's State Trees**, the behavior graph functions as a highly scalable hierarchical state architecture:
*   Decoupled tasks (`Tasks`), evaluators (`Evaluators`), and guards (`Conditions`) completely isolate calculations from the main character loop.
*   Uses persistent evaluators to transform sensory raw inputs into state tags (`Gameplay Tags`) atomizing fast state-swapping (e.g., swapping instantly from *Hear Investigation* to *Aggressive Prediction Chase*) without checking bloated recursive branches.

---

## ⚡ The Engineering Challenge: Algorithmic Noise & CPU Bounds

**The Problem:** Running real-time multizone tridimensional vision checks (dozens of line-traces per frame), processing dynamic environmental noise events (Loud, Moderate, and Soft bounds), and updating target pathfinding vectors across multiple game states was creating heavy frame latency within the game loop.

**The Solution:**
*   **Asynchronous Processing:** Centralized high-demand computations inside native C++ routines, enabling multithreaded evaluation calls isolated from the main rendering loop.
*   **Mathematical Simplifications:** Replaced heavy geometry checking with direct dot-product matrix comparisons (`Dot Product > 0.96` lookup thresholds) to verify line-of-sight alumbramientos from the flashlight system prior to launching physical raycasts.
*   **Cache Locality and Data Assets:** Abstracted state variables onto atomic Blackboard properties, preventing expensive `Casting` tasks during structural updates.
*   **Result:** Reached a locked, stable frame performance running a highly polished systemic tracking sequence with reactive post-process alerting feedback.

---

## 🛠️ Tech Stack
*   **Engine:** Unreal Engine 5 (Enhanced Input, Materials Collection, Sound Cues)
*   **Languages:** Native C++ (Core Systems), Blueprints (High-level actor triggers)
*   **Architecture:** Hierarchical State Trees, Game Systemic Director, Custom ECS Concepts
*   **Methodology:** Scrumban managed via Trello & Git versioning
