ReliefTable AI

Advanced AI-Guided Decompression & Resistance Therapy Table (No Camera)
Simulation Track — The Droids Strike Back Hackathon

Overview

ReliefTable AI is a next-generation therapy device combining spinal decompression, resistance training, gamified rehab, and AI-driven adaptive coaching. The system uses a touchscreen interface, voice-guided intake, and a full suite of sensors—including pressure pads, IMU, force sensors, and actuator encoders—to personalize therapy in real time.

This prototype simulates the software brain of a full robotic rehab table. The design is structured for low-cost mass production in China (~$65–$85 per unit) and runs on a Raspberry Pi or similar SBC. Although this is a wellness-oriented prototype and not a medical device, it demonstrates how accessible robotics and AI can improve spine care and daily rehab.

⸻

Key Features

1. Spinal Decompression Mode
	•	Low-torque actuator gently elongates the spine.
	•	Adaptive stretch limits based on:
	•	User weight range
	•	Pain reports
	•	Session history
	•	Sensor readings from pressure pads
	•	Fully interruptible at any moment via emergency bulb.

2. Resistance Training Mode
	•	Second actuator provides low-force, controlled resistance.
	•	Users can push back against the machine for:
	•	Core activation
	•	Isometric strengthening
	•	Posterior chain engagement
	•	Anti-rotation training
	•	Sensor data adjusts resistance safely and dynamically.

3. Gamified Therapy
	•	On-screen avatar mimics user movements based on:
	•	IMU readings
	•	Resistance force feedback
	•	Hand-grip or touch inputs
	•	User “ducks,” “holds,” or “braces” against obstacles.
	•	Boosts rehab compliance and motor control.

4. Voice-Guided Assistant
	•	Intake questions:
	•	Pain levels
	•	Location of discomfort
	•	Mobility limitations
	•	Prior session tolerance
	•	Mid-session safety check-ins:
	•	“Any sharp pain or numbness?”
	•	“Want to ease off?”
	•	Adaptive coaching and program adjustments.

5. Full Sensor Suite (No Camera)

Sensors allow the table to estimate alignment, compensation, and force patterns:
	•	Pressure pads (shoulders, hips, optional legs)
	•	Force sensor inline with actuator for resistance measurement
	•	IMU (table-mounted or small clip) for body orientation
	•	Actuator encoder for tracking tilt and extension
	•	Emergency squeeze bulb with pressure sensor

All sensing is non-diagnostic and intended for adaptive wellness training.

6. Touchscreen Interface
	•	7-inch capacitive screen
	•	Shows:
	•	Live stretch level
	•	Avatar game view
	•	Resistance force
	•	Weight distribution
	•	Real-time coaching
	•	Large buttons for accessibility.

7. Session Logging
	•	Program used
	•	Maximum stretch
	•	Resistance forces applied
	•	Pain checkpoints
	•	Sensor asymmetry (left/right loading)
	•	Emergency stops

Progress is tracked over time and used by the AI to tune future sessions.

⸻

Physical Design Concept

Target device specs
	•	Device weight: ~80–100 lb
	•	User weight capacity: 350 lb (scalable to 400+)
	•	Frame: laser-cut steel or aluminum
	•	Casters: lockable for repositioning
	•	Platform length: 72–78 inches
	•	Upholstery: PU leather with foam layers

Architecture 
src/
│── main.py                 # Entry point for full simulation
│── motor_controller.py     # Dual-actuator control (decompression + resistance)
│── safety_engine.py        # Maximum limits, emergency logic, pain-safe behavior
│── sensors/
│     ├── pressure_map.py   # Reads pressure pad distribution
│     ├── imu_reader.py     # Orientation & movement sensing
│     ├── force_sensor.py   # Inline strain gauge readings
│     ├── bulb_stop.py      # Emergency squeeze bulb logic
│     └── encoder.py        # Actuator position encoder
│── voice_assistant.py      # Voice intake, check-ins, adaptive adjustments
│── session_programs.py     # Decompression, resistance, and hybrid programs
│── game_engine.py          # Avatar movement & gamified tasks
│── hand_control.py         # Virtual grip / touchscreen control mapping
│── ui/
│     └── touchscreen.py    # Touch UI for therapy control & game view
│── utils/
│     ├── logger.py
│     └── math_utils.py
README.md

The system is modular so each component can be replaced with real hardware modules later.

⸻

Sensor Placement

Pressure pads (4+ zones)
	•	Left shoulder
	•	Right shoulder
	•	Left hip
	•	Right hip

IMU
	•	Under mid-back or on a small wearable clip

Force sensor
	•	Inline with resistance actuator

Actuator encoder
	•	Directly on decompression actuator

Emergency squeeze bulb
	•	Mounted near user’s hand with analog pressure sensor

⸻

Why No Camera?

To avoid medical device complexity and to maintain a low-sensor-cost architecture while still enabling:
	•	Alignment estimation
	•	Flexion/extension tracking
	•	Left/right asymmetry detection
	•	Range-of-motion measurements
	•	Resistance force profiling

All without imaging-based evaluation.

⸻

Therapy Programs

1. Decompression Program
	•	8–12 minutes
	•	Slow traction cycles
	•	Pain feedback adjusts limits automatically

2. Resistance Program
	•	5–8 minutes
	•	Push/hold cycles
	•	IMU + force data tune intensity
	•	Ideal for core + posterior chain

3. Hybrid Program
	•	Decompression → Mobility → Resistance → Cooldown
	•	Total: ~20 minutes

4. Game Mode
	•	Avatar ducks/leans based on IMU
	•	Light resistance creates challenge levels
	•	Excellent for long-term compliance

⸻

Safety Systems
	•	Emergency bulb = instant stop
	•	Auto-stop on:
	•	Sharp pain report
	•	Force sensor overload
	•	Sudden asymmetry spike
	•	Max stretch and resistance capped by:
	•	User weight
	•	Mobility profile
	•	Sensor readings

This is a wellness device and not intended to diagnose or treat medical conditions.

⸻

Manufacturing & Cost (China Mass Production)
Estimated at MOQ 1,000+:
Category
Cost (USD)
Touchscreen + SBC
$24–$40
Actuators (2)
$10–$18
Sensors (pressure, IMU, force, encoder)
$4–$9
Safety bulb + enclosure
$1.3–$2.5
Frame + upholstery
$9–$20
Assembly + packaging
$2.2–$3.6

Total: ~$65–$85 per unit fully assembled

Comparable devices retail for $399–$1,299 without robotics.

Getting Started
git clone YOUR_REPO_URL
cd ReliefTableAI
pip install -r requirements.txt
python3 src/main.py

Future Work
	•	Adaptive machine-learning pain prediction
	•	Personalized weekly training plans
	•	Bluetooth wearable clip
	•	Cloud analytics dashboard
	•	Remote therapist mode
	•	Multi-user profiles

⸻

License

MIT License (or your preferred license)

⸻

Acknowledgements

Developed for The Droids Strike Back Hackathon to demonstrate how AI, low-cost robotics, and smart sensing can create accessible, personalized rehab systems for millions of people living with chronic back pain or mobility limitations.