# Alien: Isolation AI Architecture inside Unreal Engine 5

<p align="center">
  <img src="https://img.shields.io/badge/Unreal%20Engine-5.x-blue.svg?style=for-the-badge&logo=unrealengine" alt="Unreal Engine 5">
  <img src="https://img.shields.io/badge/C%2B%2B-Native-orange.svg?style=for-the-badge&logo=c%2B%2B" alt="Native C++">
  <img src="https://img.shields.io/badge/Architecture-State%20Trees%20%26%20Director-red.svg?style=for-the-badge" alt="AI Architecture">
</p>

## 🕹️ Overview
This project is a high-performance **systemic AI testing ground developed in Unreal Engine 5**, replicating the dual-layer stalking mechanics of *Alien: Isolation*. Moving away from rigid state structures, the architecture leverages native **C++ subsystems** combined with the new **UE5 State Trees** framework to manage dynamic environmental tension and non-deterministic hunting behaviors in real-time.

---

## 📸 Systems Debugging & Media

Para validar los sistemas de ingeniería tridimensionales y la toma de decisiones no lineal, se desarrollaron herramientas de diagnóstico visual directamente sobre el viewport de ejecución:

| 🧠 Tridimensional Volumetric Raycasting (C++) | 🌲 Hierarchical State Tree Pipeline (Attack Core) |
|---|---|
| Muestra el sensor multizona desarrollado en código nativo calculando los umbrales de oclusión ambiental en tiempo real. | Estructura jerárquica que gestiona las transiciones atómicas basadas en Gameplay Tags para evitar la latencia de hilos. |
| <img src="https://github.com/user-attachments/assets/714c2a32-7d6a-4d70-8b9e-64b651fa5a7b" width="100%" alt="Vision Cones" /> | <img src="https://github.com/user-attachments/assets/33991b84-4712-4a89-9ab5-b6559d8a8aa7" width="100%" alt="State Tree Attack" /> |

### 🎯 Skeletal-Bound Perception Tracking (Amplified Senses)
Demostración técnica de cómo las matrices de los sensores ópticos se acoplan directamente al hueso de la cabeza del Skeletal Mesh, logrando que los vectores de visión sigan de forma orgánica la animación del cuello y se desacoplen por completo de la cápsula rígida de colisión del actor[cite: 2].

<p align="center">
  <img src="https://github.com/user-attachments/assets/f162e232-80a3-4ee9-b09e-ae828182d918" width="85%" alt="Skeletal Bound Perception Cone" />
</p>

---

### 🛠️ High-Level Interaction Triggers (Visual Scripting)
Mientras que los núcleos matemáticos pesados y los sensores lógicos se procesan estrictamente en C++ para garantizar la tasa de refresco, los activadores de nivel (triggers), interfaces de interactuables y eventos sutiles del escenario se delegan en scripts visuales optimizados[cite: 2].

<details>
<summary>🔍 Click here to expand the High-Level Blueprint Trigger Graph</summary>

Módulo desacoplado mediante interfaces que gestiona la física reactiva de los accesos y la propagación de rangos acústicos locales dentro del bucle sistémico[cite: 2].

<p align="center">
  <img src="https://github.com/user-attachments/assets/23be0026-6cd4-4e90-9fa1-c1cfab6fb418" width="100%" alt="Blueprint Code" />
</p>

</details>

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
