# Nuclear Chemistry 3D Simulation Architecture

## Overview
An educational Three.js-based 3D simulation for high school students to learn nuclear chemistry through interactive, scaffolded learning experiences.

## Design Decisions
- **Half-life decay curves**: Included as a sub-module in Level 2
- **Visual style**: Realistic spheres with physically accurate rendering
- **Sound effects**: Enabled for particle collisions and nuclear reactions

---

## Scaffolded Teaching Framework

### Level 1: Atomic Fundamentals (Foundation)

#### Learning Objectives
- Identify subatomic particles (protons, neutrons, electrons)
- Understand atomic structure and notation (A, Z numbers)
- Visualize isotopes vs elements

#### Simulation Features
- **Interactive atom builder**: drag protons/neutrons into nucleus
- **Real-time atomic notation display** (e.g., ²³⁵U)
- **Stability indicator** showing neutron-to-proton ratio
- Color-coded particles:
  - Protons: Red spheres
  - Neutrons: Blue spheres
  - Electrons: Yellow small spheres in orbital clouds

---

### Level 2: Radioactive Decay Types

#### Learning Objectives
- Distinguish alpha (α), beta (β), and gamma (γ) radiation
- Understand mass/charge changes in each decay type
- Predict daughter nuclei from decay equations
- **Interpret half-life decay curves**

#### Simulation Features
- Select parent isotope from periodic table subset
- Trigger decay and watch particle emission in 3D
- Track mass number and atomic number changes
- Visual particle trails with distinct colors/shapes:
  - Alpha particles: Gold/orange with helium nucleus structure
  - Beta particles: Purple streaks (high velocity)
  - Gamma rays: Green wave pulses
- **Half-life decay curve sub-module**:
  - Interactive graph showing N(t) = N₀ × (1/2)^(t/t½)
  - Adjustable time slider
  - Sample size visualization with decaying nuclei count
  - Compare half-lives of different isotopes

---

### Level 3: Scattering Experiments

#### Learning Objectives
- Understand Rutherford scattering (gold foil experiment)
- Observe elastic vs inelastic scattering
- Relate deflection angle to nuclear size/charge

#### Simulation Features
- Fire alpha particles at gold foil target
- Adjustable particle energy and impact parameter
- Real-time deflection visualization
- Statistical distribution of scattering angles (histogram)
- Toggle between:
  - Single particle mode (detailed trajectory)
  - Beam mode (statistical patterns)
- Sound effects for particle deflections (pitch varies with angle)

---

### Level 4: Nuclear Fission

#### Learning Objectives
- Understand neutron-induced fission mechanism
- Identify fission products and energy release
- Grasp chain reaction concept

#### Simulation Features
- U-235 or Pu-239 nucleus selection
- Fire neutron to trigger fission
- Watch nucleus split with daughter nuclei + neutrons
- **Chain reaction modes**:
  - Single event (educational)
  - Controlled chain (reactor simulation)
  - Uncontrolled chain (critical mass demo)
- Energy meter showing released energy (MeV)
- Control rod simulation for reactor mode
- Sound effects: Deep rumble for fission events

---

### Level 5: Nuclear Fusion

#### Learning Objectives
- Understand Coulomb barrier concept
- Identify fusion fuel cycles (D-T, p-p chain)
- Compare energy output: fusion vs fission

#### Simulation Features
- Select fusion reaction type:
  - Deuterium-Tritium (D-T)
  - Proton-Proton chain (stellar fusion)
  - Deuterium-Deuterium (D-D)
- Adjustable collision energy/temperature
- Visualize barrier penetration probability
- Show mass defect → energy conversion (E=mc²)
- Temperature gauge with plasma visualization
- Energy comparison chart: Fusion vs Fission per nucleon
- Sound effects: High-pitched resonance for successful fusion

---

## Technical Architecture

```
/src
├── core/
│   ├── SceneManager.js        # Three.js scene setup, camera, lighting
│   ├── ParticleSystem.js      # Particle physics engine & trajectories
│   ├── AtomRenderer.js        # Nucleus/electron cloud rendering
│   ├── AudioManager.js        # Sound effects system
│   └── PhysicsEngine.js       # Coulomb forces, scattering calculations
├── modules/
│   ├── Level1_AtomBuilder/
│   │   ├── AtomBuilder.js     # Drag-and-drop nucleus construction
│   │   ├── StabilityMeter.js  # N/Z ratio visualization
│   │   └── NotationDisplay.js # Atomic notation renderer
│   ├── Level2_Decay/
│   │   ├── DecaySimulator.js  # Alpha, beta, gamma decay logic
│   │   ├── ParticleEmitter.js # Decay particle visualization
│   │   ├── HalfLifeCurve.js   # Decay curve graphing sub-module
│   │   └── DecayChain.js      # Sequential decay tracking
│   ├── Level3_Scattering/
│   │   ├── RutherfordExp.js   # Gold foil experiment simulation
│   │   ├── ScatteringCalc.js  # Deflection angle calculations
│   │   └── AngleHistogram.js  # Statistical distribution display
│   ├── Level4_Fission/
│   │   ├── FissionSimulator.js    # Neutron-induced fission
│   │   ├── ChainReaction.js       # Chain reaction modes
│   │   ├── ControlRods.js         # Reactor control simulation
│   │   └── EnergyMeter.js         # Energy release visualization
│   └── Level5_Fusion/
│       ├── FusionSimulator.js     # Fusion reaction mechanics
│       ├── CoulombBarrier.js      # Barrier visualization
│       ├── PlasmaRenderer.js      # High-temperature plasma effects
│       └── EnergyComparison.js    # Fusion vs fission comparison
├── ui/
│   ├── ProgressTracker.js     # Scaffolded progress with mastery gates
│   ├── InfoPanel.js           # Context-sensitive help & equations
│   ├── QuizSystem.js          # Knowledge check assessments
│   ├── HintSystem.js          # Progressive hint reveals
│   └── ControlPanel.js        # Sliders, buttons, element selector
├── effects/
│   ├── ParticleTrails.js      # Colored trajectory trails
│   ├── GlowEffects.js         # Nuclear reaction glow
│   └── ShockwaveEffect.js     # Fission/fusion impact visuals
├── audio/
│   ├── CollisionSounds.js     # Particle collision audio
│   ├── ReactionSounds.js      # Fission/fusion audio
│   └── AmbientSounds.js       # Background audio
└── data/
    ├── isotopes.json          # Nuclear data (mass, Z, N, stability)
    ├── reactions.json         # Decay/reaction paths & products
    ├── halfLives.json         # Half-life values for isotopes
    └── energyData.json        # Binding energies, mass defects
```

---

## Scaffolding Mechanics

| Scaffold Element | Implementation |
|------------------|----------------|
| **Guided Discovery** | Hint system with progressive reveals (3 levels of hints) |
| **Mastery Gates** | Must complete quiz (70% score) to unlock next level |
| **Visual Anchors** | Consistent color coding across all levels |
| **Immediate Feedback** | Real-time equation balancing validation |
| **Complexity Fade** | Remove training wheels in later levels |
| **Audio Cues** | Sound feedback for correct/incorrect actions |
| **Progress Persistence** | LocalStorage saves student progress |

---

## Realistic Visual Style Guide

### Particle Rendering
- **Protons**: Realistic red spheres with subtle surface texture, specular highlights
- **Neutrons**: Blue-gray spheres with matte finish
- **Electrons**: Small yellow spheres with motion blur in orbitals
- **Alpha particles**: Composite He-4 nucleus with visible internal structure
- **Beta particles**: Tiny purple spheres with elongated trail effects
- **Gamma rays**: Sinusoidal wave visualization in green

### Lighting
- Three-point lighting setup for depth
- Point lights at reaction sites for energy release glow
- Ambient occlusion for realistic shadows

### Materials
- PBR (Physically Based Rendering) materials
- Metallic nuclei with appropriate roughness
- Emissive materials for high-energy particles

---

## Sound Effects Design

| Event | Sound Design |
|-------|--------------|
| Proton/Neutron placement | Soft "click" with subtle resonance |
| Successful atom build | Harmonic chime |
| Alpha decay | Deep "thump" with particle whoosh |
| Beta decay | Quick "zap" with electrical crackle |
| Gamma emission | High-frequency pulse |
| Particle scattering | Impact sound varying with angle |
| Fission event | Deep rumble with splitting crack |
| Chain reaction | Building crescendo of fission sounds |
| Fusion success | Bright resonant tone with energy release |
| Quiz correct | Positive confirmation sound |
| Quiz incorrect | Gentle error tone |

---

## UI Layout

```
┌─────────────────────────────────────────────────────────────────┐
│  [🔵 Level 1] [⚪ Level 2] [⚪ Level 3] [⚪ Level 4] [⚪ Level 5]  │  ← Progress tabs
│  Atomic Basics   Decay      Scattering   Fission     Fusion     │    (locked levels grayed)
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│                                                                 │
│                    3D SIMULATION VIEWPORT                       │
│                      (Three.js Canvas)                          │
│                                                                 │
│                                                                 │
├───────────────────────┬─────────────────────────┬───────────────┤
│  📖 Info Panel        │  🎮 Controls            │  📝 Quiz      │
│  ─────────────────    │  ─────────────────      │  ──────────   │
│  Current concept      │  [Element Selector]     │  Question 1/5 │
│  Key equations        │  Energy: [━━━━━━━━━]    │               │
│  Step-by-step guide   │  Speed:  [━━━━━━━━━]    │  [A] [B]      │
│                       │                         │  [C] [D]      │
│  💡 Hint (1/3)        │  [▶ Start] [⏸ Pause]    │               │
│                       │  [🔄 Reset] [🔊 Sound]  │  [Submit]     │
└───────────────────────┴─────────────────────────┴───────────────┘
```

---

## Assessment Structure

### Per-Level Quizzes (5 questions each)
- **Level 1**: Particle identification, atomic notation, isotope recognition
- **Level 2**: Decay type identification, daughter nuclei prediction, half-life calculations
- **Level 3**: Scattering angle prediction, experiment interpretation
- **Level 4**: Fission product identification, chain reaction concepts
- **Level 5**: Fusion conditions, energy calculations, stellar nucleosynthesis

### Mastery Requirements
- 70% minimum to unlock next level
- Unlimited retakes allowed
- Detailed feedback on incorrect answers

---

## Data Models

### Isotope Schema (isotopes.json)
```json
{
  "U-235": {
    "symbol": "U",
    "name": "Uranium",
    "atomicNumber": 92,
    "massNumber": 235,
    "neutrons": 143,
    "halfLife": 703800000,
    "halfLifeUnit": "years",
    "decayModes": ["alpha"],
    "stable": false,
    "fissile": true
  }
}
```

### Reaction Schema (reactions.json)
```json
{
  "U235_fission": {
    "type": "fission",
    "parent": "U-235",
    "trigger": "neutron",
    "products": ["Ba-141", "Kr-92"],
    "neutronReleased": 3,
    "energyMeV": 200
  }
}
```

---

## Implementation Phases

### Phase 1: Core Infrastructure
- Three.js scene setup with realistic lighting
- Particle rendering system with PBR materials
- Audio manager initialization
- UI framework and progress tracking

### Phase 2: Level 1 - Atomic Fundamentals
- Drag-and-drop atom builder
- Stability visualization
- Atomic notation display
- Level 1 quiz

### Phase 3: Level 2 - Radioactive Decay
- Decay type simulations
- Particle emission effects
- Half-life curve sub-module
- Level 2 quiz

### Phase 4: Level 3 - Scattering
- Rutherford experiment simulation
- Trajectory calculations
- Statistical histogram
- Level 3 quiz

### Phase 5: Level 4 - Fission
- Fission mechanics
- Chain reaction modes
- Control rod simulation
- Level 4 quiz

### Phase 6: Level 5 - Fusion
- Fusion reaction types
- Coulomb barrier visualization
- Plasma effects
- Level 5 quiz

### Phase 7: Polish
- Sound effect integration
- Performance optimization
- Cross-browser testing
- Accessibility features

---

## Browser Requirements
- WebGL 2.0 support
- Modern browsers (Chrome 80+, Firefox 75+, Safari 14+, Edge 80+)
- Recommended: Hardware-accelerated graphics

## Dependencies
- Three.js (r150+)
- Web Audio API (native)
- No additional frameworks required (vanilla JS)
