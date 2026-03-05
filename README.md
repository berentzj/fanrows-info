# FanRows

**Continuous Embodied Audio Interaction in the Browser**

FanRows is an experimental system for embodied interaction with sound environments.

Instead of triggering sounds through discrete gestures, FanRows continuously regulates a layered sound environment based on body posture, motion dynamics, and stability.

The system combines:

- webcam-based pose tracking
- continuous motion feature extraction
- state-based regulation logic
- layered audio environments
- scene-based interaction spaces

Together these components form a closed feedback loop between body movement and sound space.

FanRows runs entirely in the browser and is designed as a research-oriented interaction framework.

---

## Project Website
Learn more at:  
**https://fanrows.com**

---

# Table of Contents

- Introduction
- Core Idea
- Interaction Model
- System Overview
- Motion Analysis
- Regulation Layer
- Audio Engine
- Scene System
- Mapping System
- Effect System
- Visual System
- Configuration System
- Studio Environment
- External Integration
- Technical Architecture
- Example Interaction Flow
- JSON Configuration Schema
- Example Session
- Future Development
- License

---

# Introduction

## What FanRows Is

FanRows is a browser-based system for continuous embodied audio interaction.

Rather than treating gestures as discrete commands, FanRows interprets body motion as continuous signals that gradually reshape a sonic environment.

The result is an evolving sound space that reacts to posture, movement intensity, stability, and sustained spatial configurations.

FanRows combines:

- pose tracking
- motion feature extraction
- state-based interaction logic
- a layered audio engine

---

# Core Idea

Most interactive music systems follow an event-based model:

gesture → trigger → sound

FanRows instead uses continuous regulation:

motion features → regulation → sound field modulation

Movement does not execute commands.

Movement modifies the conditions of the sound environment.

---

# Interaction Model

FanRows operates as a closed feedback loop:

body movement

↓

motion analysis

↓

state regulation

↓

audio environment

↓

perception

↓

movement adaptation

The user becomes part of a dynamic system where motion and sound continuously influence each other.

---

# System Overview

FanRows consists of four main layers:

- Motion Analysis
- Regulation Layer
- Audio Engine
- Configuration System

Each layer operates continuously during interaction.

---

# Motion Analysis

FanRows uses webcam-based pose tracking.

Current implementation uses:

- MediaPipe Pose
- MediaPipe Hands (optional)

The system extracts spatial and temporal motion features such as:

- joint angles
- limb orientation
- movement velocity
- posture stability
- motion persistence

Example feature vector:

```json
{
  "velocity": 0.42,
  "stability": 0.73,
  "rightArmAngle": 0.58,
  "leftArmAngle": 0.12
}
```

These features define a continuous motion state space.

**Regulation Layer**

The regulation layer converts motion features into stable interaction states.
Instead of reacting instantly to motion, the system evaluates:

- thresholds
- persistence over time
- spatial stability
- temporal windows

Example logic:

if pose detected for > holdTime

→ pose becomes active

This prevents unstable triggers and enables smooth interaction dynamics.

**Audio Engine**

The audio engine uses a layered sound architecture. Multiple loops run simultaneously and remain synchronized.

Key characteristics:

- loops always running in sync
- gain-based activation
- BPM-synchronized playback
- continuous parameter modulation

Traditional audio engines:

- start loop
- stop loop

FanRows approach:

- loop always playing
- volume modulated

Advantages:

- seamless transitions
- no timing drift
- no playback artifacts

**Scene System**

Interaction environments are structured into sessions and scenes.

Session: A session represents a complete interaction environment containing:

- scenes
- configuration parameters
- loop definitions

**Scene**

A scene defines:

- active loops
- motion mappings
- effect mappings
- visual settings

Scenes represent bounded interaction contexts.

**Scene Transitions**

Scene transitions occur when sustained body states are detected.

Example:

arms crossed → switch scene

Transitions typically depend on pose persistence, stability thresholds, and temporal windows.

**Mapping System**

Mappings define how motion features influence sound parameters.

| Motion Feature	 | Audio Parameter         |
|------------------|-------------------------|
|velocity	         | filter cutoff           |
|pose	             | activate loop layer     |
|stability	       | reverb size             |
|limb angle	       | pitch modulation        |

Mappings operate continuously rather than through discrete triggers.

**Effect System**

FanRows supports:

- global effects
- per-layer effects
- dynamic modulation

Examples include:

- filter frequency
- reverb wet level
- chorus depth
- delay feedback

**Cue Engine**

The Cue Engine introduces controlled temporal variation, such as:

- slow parameter drift
- probabilistic modulation
- evolving scene conditions

**Visual System**

FanRows includes a visual feedback layer. Possible visual elements:

- skeleton visualization
- background videos
- abstract overlays

Visual feedback helps users understand the relationship between movement and sound response.

**Configuration System**

All interaction environments are defined through JSON configuration files.

Configuration defines:

- sessions
- scenes
- loops
- motion mappings
- effect mappings
- visuals

This enables reproducible interaction environments.

**Studio Environment**

The Studio interface provides tools to:

- configure scenes
- adjust mappings
- calibrate thresholds
- inspect pose detection

Studio functions as a development environment for interaction sessions.

**External Integration**

Future versions will expose motion features to external systems.

Planned interfaces:

- OSC
- WebSocket
- MIDI

Possible integrations:

- Ableton Live
- TouchDesigner
- Unity
- Max/MSP

**Technical Architecture**

FanRows is implemented entirely in the browser.

| Component        | Technology              |
|------------------|-------------------------|
| Audio            | Web Audio API / Tone.js |
| Motion Tracking  | MediaPipe               |
| Runtime          | JavaScript              |
| Configuration    | JSON                    |

Example Interaction Flow:

User raises arm
→ Pose detection extracts joint angles
→ Regulation layer detects sustained pose
→ Scene mapping activates sound layer
→ Audio engine modulates loop gain
→ Sound environment evolves

**JSON Configuration Schema**

Example configuration structure:

```
{
  "stackName": "Example Session",
  "stackBpm": 120,
  "scenes": [
    {
      "sceneId": "ambient",
      "loops": [
        {
          "id": "pad",
          "file": "/audio/pad.ogg",
          "fadeInTime": 2,
          "fadeOutTime": 2
        }
      ]
    }
  ]
}
```

Example Session
```
{
  "stackName": "Embodied Sound Space",
  "stackBpm": 124,
  "scenes": [
    {
      "sceneId": "ambient",
      "loops": [
        {
          "id": "drone",
          "file": "/loops/drone.ogg"
        }
      ]
    }
  ]
}
```

**Future Development**

Planned directions include:

- external media system integration
- extended visual environments
- multi-user interaction
- extended motion feature extraction
- embodied interaction API
- research data analysis tools

**License**

FanRows is currently released as a research prototype.

The source code is not publicly released at this stage.

This repository documents the system architecture and interaction model.

