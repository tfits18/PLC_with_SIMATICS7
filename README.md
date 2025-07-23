# Simple PI/PID Controllers for Siemens TIA Portal

## 📢 Overview

This repository provides simple, custom-written PI and PID controller functions for Siemens TIA Portal (versions 14, 15, and newer), compatible with S7-1200 and S7-1500 series CPUs. These functions were developed out of a need for a more straightforward, accessible, and portable control solution than the standard Siemens libraries.
---

## 🧐 The Problem

As a control technology professional frequently working in the TIA Portal environment, I found the standard Siemens modules to be consistently unsatisfactory for my needs in pressure and temperature regulation. Key issues included:

* **Library Incompatibility**: Different CPU series often require different, incompatible libraries.
* **No Simulation Support**: The inability to simulate controllers makes testing and debugging difficult.
* **Closed Source**: The source code is inaccessible, preventing modification or deep understanding.
* **High Complexity**: The learning curve is steep, requiring significant time to familiarize oneself with the functionalities.
* **Lack of Portability**: Migrating solutions to other environments like Codesys is not feasible.
* **Forced Integration**: Heavy integration within TIA Portal restricts flexible implementation.
* **Trial and Error**: A significant amount of trial and error is often needed to get the controllers to function as desired.
* **Rigid Structure**: Requires mandatory use of Cyclic OBs and Global DBs, preventing integration into more modular, private functions.
* **Overwhelming Documentation**: Manuals often span thousands of pages, making it hard to find relevant information quickly.

---

## 💡 The Solution

After failing to find a suitable alternative, I decided to create my own solution. I've rewritten core controller functions, drawing inspiration from the simplicity of the **OSCAT library**. The result is a set of lightweight, effective, and easy-to-understand PI and PID controllers that I have successfully used in my projects up to TIA Portal v20.

My goal isn't to replace every other library but to give back to the community that has provided so much valuable open-source knowledge. These functions are proven to work reliably. Please feel free to use and adapt them.

---

## 🛠️ Usage Instructions

The controller outputs a standard value ranging from **0 to 100**. For binary actuators (like a solenoid valve), you can use this output with a clock generator to achieve pulse width modulation (PWM).

* The **PI controller** is designed for standalone operation and is ideal for applications like pressure regulation.
* The **PID controller** builds on the PI controller by adding a derivative component, making it well-suited for temperature regulation.

**❗️ Important:** Always use the `ib_Reset` input to stop the controller if the regulation loop is interrupted (e.g., a pump is turned off). This action resets the integral component and prevents "integral windup," which can cause significant overshoot when the loop restarts.

### Parameters

| Parameter               | Type    | Description                                                                                                                                                    |
| ----------------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ir_Input`              | `REAL`  | **(Input)** The measured process value (e.g., current pressure or temperature).                                                                                |
| `ir_Setpoint`           | `REAL`  | **(Input)** The desired target value for the process.                                                                                                          |
| `ir_ProportionalGain`   | `REAL`  | **(Input)** The P-Gain. The error is multiplied by this factor. Higher values lead to a stronger and faster response.                                           |
| `ir_IntegrationGain`    | `REAL`  | **(Input)** The I-Gain. Determines how quickly the integral component corrects for steady-state errors. A higher value results in a faster-changing integral. |
| `ir_DerviateGain`       | `REAL`  | **(Input)** The D-Gain. Multiplies the rate of change of the error. A higher value results in a stronger differential response to sudden changes.              |
| `ir_DerviateActionTime` | `REAL`  | **(Input)** The time (in seconds) until the differential response has halved. A higher value results in a longer-lasting differential effect.                  |
| `ib_Reset`              | `BOOL`  | **(Input)** When `TRUE`, the integral is cleared, and the output is set to zero.                                                                               |
| `or_Output`             | `REAL`  | **(Output)** The controller output value in percent (0-100).                                                                                                   |

**Note for Large Systems:** If your control system is extremely large or has very long cycle times, it is recommended to call the PI or PID module cyclically **every second**. This prevents the internal floating-point numbers used for time calculation from becoming too small, which could lead to calculation errors.

---

## ⚙️ Installation

Installation is very simple:

1.  In your TIA Portal project tree, navigate to **External source files**.
2.  Add the two provided `.scl` files to this folder.
3.  Right-click on the source files and select **"Generate blocks from source"**. The functions will then be available in your project.

---

## ➡️ Porting to Other Systems

Porting this logic to other PLC platforms like Step-7 Classic or Codesys is straightforward. The core control logic is as follows:

```scl
// Proportional Component
#Controller_Response_Proportional := #ir_ProportionalGain * (#ir_Setpoint - #ir_Input);

// Integral Component
#Controller_Response_Integral += #ir_IntegrationGain * (#ir_Setpoint - #ir_Input) * #PastTime;

// Derivative Component
#Intermediate_value += (#ir_SetpointDiverence - #Intermediate_value) * #PastTime / #ir_DerivateActionTime;
#or_Output := (#ir_SetpointDiverence - #Intermediate_value) * #ir_DerivateGain;
