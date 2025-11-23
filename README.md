# ReliefFlow-AI
AI-Driven Therapeutic Back Stretching System
ReliefTable AI

Voice-Controlled Robotic Spinal Decompression Simulator
Simulation Track — The Droids Strike Back Hackathon

Overview

ReliefTable AI is a simulation of an AI-guided robotic spinal decompression device designed for people with back injuries, weak arm strength, or limited mobility. The system uses voice interaction, adaptive safety rules, and a virtual hand-grip controller to adjust traction intensity in real time.

This prototype represents the software brain of a future therapeutic robotics platform. It is structured to run on a Raspberry Pi (or any Python environment) and simulates how a physical decompression table or stand-assist recliner would behave when powered by motors, sensors, and safety logic.

Note: This is a hackathon prototype and not a medical device. It is not intended for diagnostic or therapeutic use.

⸻

Key Features

1. Voice-Controlled Assistant
	•	Guides users through an intake process.
	•	Collects:
	•	Pain level (0–10)
	•	Pain location
	•	Mobility limitations
	•	Ongoing discomfort
	•	Checks in during sessions:
	•	“How does this feel?”
	•	“Any sharp pain or numbness?”
	•	Adjusts program intensity or pauses based on user feedback.

2. Real-Time Stretch Control (Simulated Robotics)
	•	Uses a simulated “hand opening” input (0.0–1.0).
	•	Maps hand openness to stretch intensity (0–10).
	•	Ramp-up and ramp-down motion smoothing.
	•	Enforces safe limits based on injury type and weight range.

3. Safety-First Design
	•	Maximum stretch limits strictly enforced.
	•	High-priority Emergency Stop:
	•	Immediately halts motion
	•	Returns to neutral position
	•	Locks system until reset
	•	Auto-stop triggered by dangerous feedback such as sharp pain.

4. Raspberry Pi-Ready Architecture

Python modules are designed for easy GPIO integration with:
	•	Linear actuators
	•	Motor drivers
	•	Emergency stop switches
	•	Analog sensors (hand grip, flex sensor, etc.)

Currently operates entirely in simulation mode, but motor interfaces are abstracted for future hardware.

5. Built-In Stretching Programs
	•	Very Gentle Low Back
	•	Gentle Full Back
	•	Recline Only

Each program runs as a step-based loop so emergency input can interrupt safely.

6. Session History
	•	Logs session details:
	•	Program used
	•	Max stretch level
	•	Pain reports
	•	Emergency events
	•	Useful for rehabilitation analytics in future versions.

Architecture
src/
│── main.py                 # Entry point
│── motor_controller.py     # Simulated motor driver + GPIO placeholders
│── safety_engine.py        # Safety rules, pain logic, max stretch limits
│── voice_assistant.py      # Intake + conversational guidance layer
│── hand_control.py         # Maps hand opening to stretch levels
│── session_programs.py     # Preset rehabilitation/stretch programs
│── emergency_stop.py       # Emergency stop handler
│── utils/
│     └── logger.py         # Simple logging utility
README.md

Each component is modular so hardware integration, voice upgrades, or safety refinements can be done without restructuring the whole project.

⸻

Getting Started

Requirements
	•	Python 3.8+
	•	(Optional) Raspberry Pi OS
	•	No physical hardware needed

  Install
  git clone YOUR_REPO_URL_HERE
cd ReliefTableAI
pip install -r requirements.txt

Run Simulation
python3 src/main.py

You will see a CLI menu with options to:
	•	Start a session
	•	Simulate hand control
	•	Trigger emergency stop
	•	Run preset programs

⸻

Voice Interaction

The voice system in this prototype uses text input/output for portability but is designed with clear extension points for:
	•	Speech-to-text API
	•	Text-to-speech engine (e.g., ElevenLabs)
	•	Local voice models on Raspberry Pi

Voice logic is contained in one module so swapping in real TTS/STT services is simple.

⸻

Hardware Integration (Future Work)

To turn this into a physical device:
	•	Replace simulated motor methods with:
	•	GPIO PWM signals
	•	Motor driver modules
	•	Relay modules
	•	Add a physical emergency stop switch (normally closed circuit)
	•	Add a grip sensor via MCP3008 ADC (or flex/glove sensor)
	•	Replace CLI with touchscreen UI or voice-only operation

The current architecture supports all of these upgrades.
