# WoR Worlds – Robotarm Simulatie

Een ROS2-simulatie van een robotarm met een virtuele servo-controller en interactie met een virtueel bekertje.
Dit project is ontwikkeld als demonstratie-omgeving waarin een robotarm realistische bewegingen uitvoert en objecten kan oppakken, bewegen en loslaten.

---

## 📦 Installatie

Zorg dat je **ROS2 Humble Hawksbill** hebt geïnstalleerd.

Maak vervolgens een workspace en plaats de repository daarin:

```bash
mkdir ros2_ws
cd ros2_ws
git clone https://github.com/MikeAckerschott/Robotic-arm-simulation.git wor__worlds_simulatie
```

Installeer afhankelijkheden en build het project:

```bash
cd ros2_ws
. /opt/ros/humble/setup.bash
rosdep install -i --from-path ./wor__worlds_simulatie/ --rosdistro humble -y
colcon build
```

---

## ▶️ Simulatie starten

Open een terminal in je workspace en source de installatie:

```bash
cd ros2_ws
. install/setup.bash
ros2 launch simple_sim_movement display.launch.py
```

Dit opent **RViz** en twee terminals:

* **Terminal 1:** visualisatie van de robotarm, het bekertje en RViz zelf
* **Terminal 2:** invoer van commando’s voor de robotarm

---

## 🎮 Robotarm aansturen

Commando’s worden gegeven in het **SSC-32U** formaat.

### Voorbeeld: één servo bewegen

```bash
#0 P2500 T3000
```

→ Servo 0 beweegt naar PWM 2500 in 3 seconden

```bash
#0 P2500 S500
```

→ Servo 0 beweegt naar PWM 2500 met snelheid 500

### Voorbeeld: meerdere servo’s tegelijk

```bash
#0 P1500 #1 P1500 #2 P1500 #3 P1500 #4 P500 #5 P1500 T3000
```

→ Beweegt de arm naar een "ready"-positie in 3 seconden

---

## 🤖 Demo-script

Een demo is aanwezig waarin de arm een bekertje oppakt, beweegt, laat vallen en terugplaatst.

Start de simulatie en voer in een **nieuwe terminal** uit:

```bash
cd ros2_ws
. install/setup.bash
./wor__worlds_simulatie/demo.sh
```

---


## 🔧 Technische details

* **ROS2 distributie:** Humble Hawksbill
* **Programmeertaal:** C++ (OOP, ROS2 style guide)
* **Visualisatie:** RViz + URDF + STL
* **Topics:**

  * `/robot_command` → bewegingen robotarm
  * `/cup_pos` → positie bekertje
  * `/cup_speed` → snelheid bekertje

---

## 👨‍💻 Auteur

**Mike Ackerschott**
📅 26 oktober 2023
