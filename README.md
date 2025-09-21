<h1>ExpNo 1 :Developing AI Agent with PEAS Description</h1>
<h3>Name: S DESHNAA </h3>
<h3>Register Number: 212224210003</h3>


<h3>AIM:</h3>
<br>
<p>To find the PEAS description for the given AI problem and develop an AI agent.</p>
<br>
<h3>Theory</h3>
<h3>Medicine prescribing agent:</h3>
<p>Such this agent prescribes medicine for fever (greater than 98.5 degrees) which we consider here as unhealthy, by the user temperature input, and another environment is rooms in the hospital (two rooms). This agent has to consider two factors one is room location and an unhealthy patient in a random room, the agent has to move from one room to another to check and treat the unhealthy person. The performance of the agent is calculated by incrementing performance and each time after treating in one room again it has to check another room so that the movement causes the agent to reduce its performance. Hence, agents prescribe medicine to unhealthy.</p>
<hr>
<h3>PEAS DESCRIPTION:</h3>
<table>
  <tr>
    <td><strong>Agent Type</strong></td>
    <td><strong>Performance</strong></td>
     <td><strong>Environment</strong></td>
    <td><strong>Actuators</strong></td>
    <td><strong>Sensors</strong></td>
  </tr>
    <tr>
    <td><strong>Medicine prescribing agent</strong></td>
    <td><strong>Treating unhealthy, agent movement</strong></td>
     <td><strong>Rooms, Patient</strong></td>
    <td><strong>Medicine, Treatment</strong></td>
    <td><strong>Location, Temperature of patient</strong></td>
  </tr>
</table>
<hr>
<H3>DESIGN STEPS</H3>
<h3>STEP 1:Identifying the input:</h3>
<p>Temperature from patients, Location.</p>
<h3>STEP 2:Identifying the output:</h3>
<p>Prescribe medicine if the patient in a random has a fever.</p>
<h3>STEP 3:Developing the PEAS description:</h3>
<p>PEAS description is developed by the performance, environment, actuators, and sensors in an agent.</p>
<h3>STEP 4:Implementing the AI agent:</h3>
<p>Treat unhealthy patients in each room. And check for the unhealthy patients in random room</p>
<h3>STEP 5:</h3>
<p>Measure the performance parameters: For each treatment performance incremented, for each movement performance decremented</p>

## Program
```
import random
import time

class HospitalEnvironment:
    def __init__(self):
        # Two rooms with random patient temperatures
        self.rooms = {
            "A": random.uniform(97.0, 102.0),  # patient in Room A
            "B": random.uniform(97.0, 102.0)   # patient in Room B
        }

    def sense_temperature(self, room):
        return self.rooms[room]

    def treat_patient(self, room):
        # After treatment, reset temperature to healthy
        self.rooms[room] = random.uniform(97.0, 98.5)


class FeverAgent:
    def __init__(self, environment):
        self.env = environment
        self.current_room = "A"  # start in Room A
        self.performance = 0

    def step(self):
        # Sense patient temperature in current room
        temp = self.env.sense_temperature(self.current_room)
        print(f"Agent in Room {self.current_room}, Patient Temp: {temp:.2f}°F")

        # Check and treat if unhealthy
        if temp > 98.5:
            print("⚕ Prescribed medicine (fever detected).")
            self.env.treat_patient(self.current_room)
            self.performance += 1
        else:
            print(" Patient healthy, no treatment needed.")

        # Move to the other room
        old_room = self.current_room
        self.current_room = "B" if self.current_room == "A" else "A"
        print(f"Moving from Room {old_room} to Room {self.current_room}")
        self.performance -= 1

        print(f"Current Performance Score: {self.performance}\n")


# --- Simulation Run ---
hospital = HospitalEnvironment()
agent = FeverAgent(hospital)

# Run for 6 steps (3 cycles through both rooms)
for _ in range(6):
    agent.step()
    time.sleep(1)
```

# Result:
The PEAS framework helps in systematically designing AI agents by defining performance measures, environment, actuators, and sensors. It ensures clarity, efficiency, and adaptability in developing agents for real-world applications.
