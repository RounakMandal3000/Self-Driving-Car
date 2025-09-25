
# 🚗 AI for Self-Driving Car

This project implements a **Deep Q-Learning agent** that learns to drive a car inside a simulated 2D environment. The environment is built using **Kivy** for visualization and interaction, while **PyTorch** powers the reinforcement learning model.

The agent perceives the environment through **3 sensors** and makes driving decisions (turn left, right, or go straight) to reach goals while avoiding obstacles drawn by the user.

---

## ✨ Features

* Neural Network powered **Deep Q-Learning** agent.
* Interactive 2D simulation built with **Kivy**.
* Ability to **draw custom maps** (roads, obstacles) with the mouse.
* **Experience Replay** for stable training.
* Save and load the trained model for later use.
* Visual debugging with sensor signals.

---

## 📂 Project Structure

```
├── ai.py        # Deep Q-Learning implementation (PyTorch)
├── map.py       # Environment & simulation (Kivy)
├── last_brain.pth  # Saved model (created after training, optional)
└── README.md    # Documentation
```

---

## ⚙️ Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/<your-username>/self-driving-car-ai.git
   cd self-driving-car-ai
   ```

2. Install dependencies:

   ```bash
   pip install torch numpy matplotlib kivy
   ```

---

## 🚀 Usage

Run the simulation:

```bash
python map.py
```

Controls:

* **Draw roads/obstacles**: Left-click and drag on the canvas.
* **Clear map**: Press the `clear` button.
* **Save model**: Press the `save` button (saves brain to `last_brain.pth`).
* **Load model**: Press the `load` button to reload the saved brain.

The car will start learning to navigate toward goals while avoiding sand (obstacles).

---

## 🧠 How It Works

1. **State representation**:
   The car observes its environment using:

   * 3 sensor signals (distance to sand).
   * Orientation relative to the goal.
   * Inverse orientation.

   → Total **5 input features**.

2. **Actions**:

   * `0`: Go straight.
   * `1`: Turn left.
   * `2`: Turn right.

3. **Rewards**:

   * `-1` if on sand or hits a boundary.
   * `-0.2` for normal movement.
   * `+0.1` when moving closer to the goal.

4. **Learning**:
   The agent updates its policy using **Deep Q-Learning** with experience replay and Adam optimizer.

---

## 📊 Training Progress

* The reward history is stored in `scores`.
* When you save the model, a training curve is plotted using matplotlib.

---

## 🔮 Future Improvements

* Add more sensors for complex navigation.
* Support continuous actions (via policy gradients).
* Experiment with convolutional inputs (images instead of sensor rays).
* Replace Kivy with PyGame or Unity for richer environments.

---

## 📝 License

This project is licensed under the MIT License.

