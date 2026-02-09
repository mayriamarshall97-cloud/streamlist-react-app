// StreamList React App (Week 1 – Program Design)
// This starter app satisfies the Week 1 requirements:
// - React Router navigation
// - StreamList homepage with user input logged to console
// - Placeholder pages for Movies, Cart, and About
// - Basic CSS styling

// =======================
// src/index.js
// =======================
import React from "react";
import ReactDOM from "react-dom/client";
import { BrowserRouter } from "react-router-dom";
import App from "./App";
import "./styles.css";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);

// =======================
// src/App.js
// =======================
import React from "react";
import { Routes, Route } from "react-router-dom";
import Navbar from "./components/Navbar";
import StreamList from "./pages/StreamList";
import Movies from "./pages/Movies";
import Cart from "./pages/Cart";
import About from "./pages/About";

function App() {
  return (
    <div className="app-container">
      <Navbar />
      <Routes>
        <Route path="/" element={<StreamList />} />
        <Route path="/movies" element={<Movies />} />
        <Route path="/cart" element={<Cart />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </div>
  );
}

export default App;

// =======================
// src/components/Navbar.js
// =======================
import React from "react";
import { NavLink } from "react-router-dom";

function Navbar() {
  return (
    <nav className="navbar">
      <h1 className="logo">🎬 StreamList</h1>
      <div className="nav-links">
        <NavLink to="/" end>StreamList</NavLink>
        <NavLink to="/movies">Movies</NavLink>
        <NavLink to="/cart">Cart</NavLink>
        <NavLink to="/about">About</NavLink>
      </div>
    </nav>
  );
}

export default Navbar;

// =======================
// src/pages/StreamList.js
// =======================
import React, { useState } from "react";

function StreamList() {
  const [item, setItem] = useState("");

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log("User Stream Item:", item);
    setItem("");
  };

  return (
    <div className="page">
      <h2>My StreamList</h2>
      <p>Add a movie or show you want to watch.</p>

      <form onSubmit={handleSubmit} className="form">
        <input
          type="text"
          value={item}
          onChange={(e) => setItem(e.target.value)}
          placeholder="Enter a movie or show"
          required
        />
        <button type="submit">Add</button>
      </form>
    </div>
  );
}

export default StreamList;

// =======================
// src/pages/Movies.js
// =======================
import React from "react";

function Movies() {
  return (
    <div className="page">
      <h2>Movies</h2>
      <p>This page will be developed in Week 4.</p>
    </div>
  );
}

export default Movies;

// =======================
// src/pages/Cart.js
// =======================
import React from "react";

function Cart() {
  return (
    <div className="page">
      <h2>Cart</h2>
      <p>This page will be developed in Week 4.</p>
    </div>
  );
}

export default Cart;

// =======================
// src/pages/About.js
// =======================
import React from "react";

function About() {
  return (
    <div className="page">
      <h2>About StreamList</h2>
      <p>This page will be developed in Week 5.</p>
    </div>
  );
}

export default About;

// =======================
// src/styles.css
// =======================
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background-color: #f4f6f8;
}

.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 30px;
  background-color: #1e1e2f;
}

.logo {
  color: #ffffff;
  margin: 0;
}

.nav-links a {
  color: #cccccc;
  margin-left: 20px;
  text-decoration: none;
  font-weight: bold;
}

.nav-links a.active {
  color: #ffffff;
}

.page {
  padding: 40px;
}

.form {
  margin-top: 20px;
}

.form input {
  padding: 10px;
  width: 250px;
  margin-right: 10px;
}

.form button {
  padding: 10px 15px;
  background-color: #4caf50;
  color: white;
  border: none;
  cursor: pointer;
}

.form button:hover {
  background-color: #43a047;
}
