# Ex06 BMI Calculator

```
NAME: V. POOJAA SREE
REG. NO: 212223040147

```

## Date:

## AIM:
To create a BMI calculator using React Router 

## ALGORITHM:
### STEP 1 State Initialization
Manage the current page (Home or Calculator) using React Router.

### STEP 2 User Input
Accept weight and height inputs from the user.

### STEP 3 BMI Calculation
Calculate the BMI based on user input.

### STEP 4 Categorization
Classify the BMI result into categories (Underweight, Normal weight, Overweight, Obesity).

### STEP 5 Navigation
Navigate between pages using React Router.

## PROGRAM:

```
App.jsx

import React from "react";
import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom";
import Home from "./Home";
import BMICalculator from "./BMICalculator";

export default function App() {
  return (
    <Router>
      <div style={{ fontFamily: "Arial, sans-serif", backgroundColor: "#f0f8ff", minHeight: "100vh", padding: "20px" }}>
        <nav style={{ backgroundColor: "#4caf50", padding: "10px 20px", borderRadius: "8px" }}>
          <Link to="/" style={{ color: "white", marginRight: "15px", textDecoration: "none", fontWeight: "bold" }}>🏠 Home</Link>
          <Link to="/calculator" style={{ color: "white", textDecoration: "none", fontWeight: "bold" }}>🧮 BMI Calculator</Link>
        </nav>

        <div style={{ marginTop: "30px", backgroundColor: "white", padding: "30px", borderRadius: "12px", boxShadow: "0 4px 10px rgba(0,0,0,0.1)" }}>
          <Routes>
            <Route path="/" element={<Home />} />
            <Route path="/calculator" element={<BMICalculator />} />
          </Routes>
        </div>
      </div>
    </Router>
  );
}

```

---

```
Home.jsx

import React from "react";

export default function Home() {
  return (
    <div style={{ textAlign: "center" }}>
      <h1 style={{ color: "#4caf50" }}>Welcome to the BMI Calculator App 💪</h1>
      <p style={{ fontSize: "18px" }}>Track your fitness by calculating your Body Mass Index.</p>
      <p>Click on "BMI Calculator" above to get started.</p>
    </div>
  );
}

```

---

```
BMICalculator.jsx

import React, { useState } from "react";

export default function BMICalculator() {
  const [weight, setWeight] = useState("");
  const [height, setHeight] = useState("");
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState("");

  const calculateBMI = () => {
    if (!weight || !height) {
      alert("Please fill out both fields");
      return;
    }

    const heightInMeters = height / 100;
    const bmiValue = weight / (heightInMeters * heightInMeters);
    const rounded = bmiValue.toFixed(2);
    setBmi(rounded);

    if (bmiValue < 18.5) setCategory("Underweight");
    else if (bmiValue < 24.9) setCategory("Normal weight");
    else if (bmiValue < 29.9) setCategory("Overweight");
    else setCategory("Obese");
  };

  return (
    <div>
      <h2 style={{ color: "#4caf50", textAlign: "center" }}>BMI Calculator 🧮</h2>

      <div style={{ maxWidth: "400px", margin: "0 auto", textAlign: "center" }}>
        <input
          type="number"
          placeholder="Enter weight (kg)"
          value={weight}
          onChange={(e) => setWeight(e.target.value)}
          style={{ padding: "10px", width: "80%", marginBottom: "15px", borderRadius: "6px", border: "1px solid #ccc" }}
        />
        <br />
        <input
          type="number"
          placeholder="Enter height (cm)"
          value={height}
          onChange={(e) => setHeight(e.target.value)}
          style={{ padding: "10px", width: "80%", marginBottom: "15px", borderRadius: "6px", border: "1px solid #ccc" }}
        />
        <br />
        <button
          onClick={calculateBMI}
          style={{ padding: "10px 20px", backgroundColor: "#4caf50", color: "white", border: "none", borderRadius: "6px", cursor: "pointer" }}
        >
          Calculate
        </button>

        {bmi && (
          <div style={{ marginTop: "20px", padding: "15px", backgroundColor: "#e8f5e9", borderRadius: "10px" }}>
            <h3>Your BMI: {bmi}</h3>
            <p style={{ fontWeight: "bold" }}>Category: {category}</p>
          </div>
        )}
      </div>
    </div>
  );
}

```

## OUTPUT:

![o1](https://github.com/user-attachments/assets/907891bb-eda6-4188-a287-40e36d0565fa)

---

![o2](https://github.com/user-attachments/assets/6e596fc0-3956-4465-9803-d7fc2f70e598)

---

## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
