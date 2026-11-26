# EXPERIMENT 1: MEASUREMENT OF FIBER OPTIC LOSS - SIMULATION

## AIM
To measure propagation loss and bending losses for two different wavelengths in plastic optical fiber using Python simulation.

---

## SOFTWARE REQUIRED
- Python 3.x
- Python IDE


## PROCEDURE

1.Import the required Python libraries, namely NumPy, Pandas, and Matplotlib, for calculations, tabulation, and plotting graphs.

2.Define the fiber lengths, input and output amplitudes, and bending diameters with their corresponding input and output amplitudes.

3.Calculate propagation loss for different fiber lengths using the input and output amplitudes.

4.Calculate bending loss for different bending diameters using the corresponding input and output amplitudes.

5.Display the calculated propagation and bending losses in tabular form using Pandas DataFrames.

6.Generate sinusoidal waveforms to compare input and output signals for different fiber lengths and bending diameters.

7.Plot the graphs with appropriate titles, axis labels, legends, and grid lines, and observe the variation in optical signal loss.

## PROGRAM

```

import math
import matplotlib.pyplot as plt

# Fiber lengths in meters
L1 = 1
L2 = 3

# -------- 660 nm --------
V1_660 = 2.00
V2_660 = 1.65

a_660 = math.log(V1_660 / V2_660) / (L2 - L1)
db_660 = a_660 * 8.686 * 1000

# -------- 950 nm --------
V1_950 = 2.00
V2_950 = 1.75

a_950 = math.log(V1_950 / V2_950) / (L2 - L1)
db_950 = a_950 * 8.686 * 1000

# Display propagation loss results
print("EXPERIMENT 1: FIBER OPTIC LOSS")
print("--------------------------------")
print("Wavelength: 660 nm")
print("Attenuation =", round(a_660, 4), "nepers/m")
print("Loss =", round(db_660, 2), "dB/km")

print("\nWavelength: 950 nm")
print("Attenuation =", round(a_950, 4), "nepers/m")
print("Loss =", round(db_950, 2), "dB/km")

# Propagation loss graph
lengths = [L1, L2]

plt.figure(figsize=(7, 4))
plt.plot(lengths, [V1_660, V2_660], 'o-', label='660 nm')
plt.plot(lengths, [V1_950, V2_950], 's-', label='950 nm')
plt.xlabel("Fiber Length (m)")
plt.ylabel("Received Voltage (V)")
plt.title("Propagation Loss in Optical Fiber")
plt.grid(True)
plt.legend()
plt.show()

# -------- BENDING LOSS --------
diameter = [10, 8, 6, 4, 2, 1]
input_voltage = [2.00] * 6
output_voltage = [1.95, 1.90, 1.82, 1.65, 1.30, 0.90]

print("\nBENDING LOSS MEASUREMENTS")
print("--------------------------------")
print("Diameter(cm)  Input(V)  Output(V)")

for d, vi, vo in zip(diameter, input_voltage, output_voltage):
    print(f"{d:8}      {vi:.2f}      {vo:.2f}")

# Bending loss graph
plt.figure(figsize=(7, 4))
plt.plot(diameter, output_voltage, 'o-', color='blue')
plt.xlabel("Loop Diameter (cm)")
plt.ylabel("Received Signal Amplitude (V)")
plt.title("Bending Loss vs Loop Diameter")
plt.grid(True)
plt.gca().invert_xaxis()
plt.show()

print("\nRESULT:")
print("Propagation loss and bending loss were simulated.")
print("Received voltage generally decreases with smaller")
print("fiber loop diameters.")
```

## OBSERVATION

### Propagation Loss
<img width="1361" height="1080" alt="image" src="https://github.com/user-attachments/assets/f120ddcc-b6fe-4a66-a4dc-6d75dd70146a" />
<img width="886" height="715" alt="image" src="https://github.com/user-attachments/assets/795d8025-7a2e-4bd5-bab4-0ef392cfd445" />


### Bending Loss
<img width="1600" height="1398" alt="image" src="https://github.com/user-attachments/assets/39dc70a9-c568-4ee3-84a4-7dc4f627f60e" />
<img width="1599" height="504" alt="image" src="https://github.com/user-attachments/assets/e6ae50b8-e185-4f8a-ac6d-bb01852cc4d4" />
<img width="932" height="750" alt="image" src="https://github.com/user-attachments/assets/fc6179d4-6de9-4949-98c8-e29cc0635b3b" />

---

## RESULT
- Propagation loss and bending losses for **660nm** and **950nm** wavelengths were measured.  
- Attenuation values compared and bending loss characteristics plotted.  
