1
import sys
import matplotlib
matplotlib.use('Agg')

import pandas as pd
import matplotlib.pyplot as plt
from scipy import stats
import io

# Creating a synthetic dataset for demonstration
data = {
    "Average_Pulse": [60, 65, 70, 75, 80, 85, 90, 95, 100, 105],
    "Calorie_Burnage": [100, 120, 130, 150, 160, 180, 200, 220, 240, 250]
}

synthetic_health_data = pd.DataFrame(data)

x = synthetic_health_data["Average_Pulse"]
y = synthetic_health_data["Calorie_Burnage"]

slope, intercept, r, p, std_err = stats.linregress(x, y)

def myfunc(x):
    return slope * x + intercept

mymodel = list(map(myfunc, x))

plt.scatter(x, y)
plt.plot(x, mymodel)
plt.ylim(ymin=0, ymax=300)
plt.xlim(xmin=0, xmax=120)
plt.xlabel("Average_Pulse")
plt.ylabel("Calorie_Burnage")
plt.show()

# Saving the plot to a buffer and flushing to stdout
buffer = io.BytesIO()
plt.savefig(buffer, format='png')
buffer.seek(0)
sys.stdout.buffer.write(buffer.read())
sys.stdout.flush() 

2
import numpy as np

# Creating a synthetic dataset for demonstration
np.random.seed(42)
average_pulse_values = np.array([120, 130, 150, 180])
calorie_burnage_predicted = 0.3296 * average_pulse_values + 346.8662

print("Average Pulse | Predicted Calorie Burnage")
print("---------------------------------------")
for i in range(len(average_pulse_values)):
    print(f"{average_pulse_values[i]:<13}
{calorie_burnage_predicted[i]:.2f}")

3
import sys
import matplotlib
matplotlib.use('Agg')

import pandas as pd
import matplotlib.pyplot as plt
from scipy import stats
import io

# Creating a synthetic dataset for demonstration
data = {
    "Duration": [15, 30, 45, 60, 75, 90, 105, 120, 135, 150],
    "Calorie_Burnage": [80, 120, 160, 200, 240, 280, 320, 360, 400, 440]
}

synthetic_health_data = pd.DataFrame(data)

x = synthetic_health_data["Duration"]
y = synthetic_health_data["Calorie_Burnage"]

slope, intercept, r, p, std_err = stats.linregress(x, y)

def myfunc(x):
    return slope * x + intercept

mymodel = list(map(myfunc, x))

print(mymodel)

plt.scatter(x, y)
plt.plot(x, mymodel)
plt.ylim(ymin=0, ymax=500)
plt.xlim(xmin=0, xmax=160)
plt.xlabel("Duration")
plt.ylabel("Calorie_Burnage")
plt.show()

# Saving the plot to a buffer and flushing to stdout
buffer = io.BytesIO()
plt.savefig(buffer, format='png')
buffer.seek(0)
sys.stdout.buffer.write(buffer.read())
sys.stdout.flush() 

4
import numpy as np

# Creating a synthetic dataset for demonstration
np.random.seed(42)
average_pulse_values = np.random.randint(100, 180, 3)
duration_values = np.random.randint(20, 70, 3)

calorie_burnage_predicted = 3.1695 * average_pulse_values + 5.8434 * duration_values - 334.5194

print("Average Pulse | Duration | Predicted Calorie Burnage")
print("---------------------------------------------------")
for i in range(len(average_pulse_values)):
    print(f"{average_pulse_values[i]:<13} | {duration_values[i]:<8} | {calorie_burnage_predicted[i]:.2f}")
