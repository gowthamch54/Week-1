# Week-1
talk about your project briefly.

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>⚡ Electric Drive — EV Explorer</title>
  <style>
    body {font-family: Arial, sans-serif;margin:0;padding:0;background:#f7f9fb;color:#333;}
    header {background:#0a3d62;color:#fff;text-align:center;padding:15px 0;}
    nav a {color:#fff;margin:0 10px;text-decoration:none;font-weight:bold;}
    nav a:hover {text-decoration:underline;}
    section {padding:40px 20px;}
    footer {background:#0a3d62;color:white;text-align:center;padding:10px 0;margin-top:30px;}

    /* Hero Section */
    .hero {text-align:center;padding:80px 20px;background:linear-gradient(120deg,#1abc9c,#16a085);color:white;}
    .btn {background:#fff;color:#16a085;padding:10px 20px;border-radius:5px;text-decoration:none;}
    .btn:hover {background:#e8f8f5;}

    /* Model Cards */
    .models-section {display:flex;flex-wrap:wrap;justify-content:center;gap:20px;}
    .model-card {background:#fff;box-shadow:0 0 10px rgba(0,0,0,0.1);padding:20px;border-radius:10px;width:260px;text-align:center;}
    .model-card:hover {transform:scale(1.03);transition:0.2s;}

    /* Chatbot */
    .chatbox {max-width:600px;margin:30px auto;border:1px solid #ddd;background:white;border-radius:10px;padding:15px;}
    .chat-output {height:300px;overflow-y:auto;border-bottom:1px solid #ddd;padding-bottom:10px;}
    .chat-input {display:flex;margin-top:10px;}
    .chat-input input {flex:1;padding:10px;}
    .chat-input button {padding:10px 20px;background:#1abc9c;border:none;color:white;}

    /* Contact */
    .contact {text-align:center;}
    form {max-width:400px;margin:auto;display:flex;flex-direction:column;}
    input,textarea {margin:10px 0;padding:10px;border:1px solid #ccc;border-radius:5px;}
    button {padding:10px;background:#1abc9c;color:white;border:none;border-radius:5px;}
  </style>
</head>
<body>

  <header>
    <h1>⚡ Electric Drive</h1>
    <nav>
      <a href="#home">Home</a>
      <a href="#models">Models</a>
      <a href="#chatbot">Chatbot</a>
      <a href="#contact">Contact</a>
    </nav>
  </header>

  <!-- HOME -->
  <section id="home" class="hero">
    <h2>Welcome to the Future of Mobility</h2>
    <p>Explore, Compare, and Learn about the latest Electric Vehicles.</p>
    <a href="#models" class="btn">View EV Models</a>
  </section>

  <!-- MODELS -->
  <section id="models">
    <h2 style="text-align:center;">🚗 Electric Vehicle Models</h2>
    <div id="models-container" class="models-section"></div>
  </section>

  <!-- CHATBOT -->
  <section id="chatbot">
    <h2 style="text-align:center;">💬 EV Assistant Chatbot</h2>
    <div class="chatbox">
      <div id="chat-output" class="chat-output"></div>
      <div class="chat-input">
        <input type="text" id="user-input" placeholder="Ask about EVs...">
        <button onclick="sendMessage()">Send</button>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact" class="contact">
    <h2>📞 Contact Us</h2>
    <form onsubmit="event.preventDefault(); alert('Thank you! We will contact you soon.');">
      <input type="text" placeholder="Your Name" required>
      <input type="email" placeholder="Email Address" required>
      <textarea placeholder="Your Message" required></textarea>
      <button type="submit">Submit</button>
    </form>
  </section>

  <footer>
    <p>© 2025 Electric Drive | Designed by [Your Name]</p>
  </footer>

  <!-- JAVASCRIPT -->
  <script>
    /* ===== EV Dataset ===== */
    const evData = [
      {"model":"Tata Nexon EV","range":"312 km","price":"₹14.5 Lakh","charging_time":"60 min (fast charge)"},
      {"model":"MG ZS EV","range":"461 km","price":"₹22.9 Lakh","charging_time":"50 min (fast charge)"},
      {"model":"Hyundai Kona Electric","range":"452 km","price":"₹23.8 Lakh","charging_time":"57 min (fast charge)"},
      {"model":"Mahindra XUV400","range":"375 km","price":"₹16.0 Lakh","charging_time":"50 min (fast charge)"}
    ];

    /* ===== Load EV Models ===== */
    const container = document.getElementById("models-container");
    evData.forEach(ev => {
      const card = document.createElement("div");
      card.classList.add("model-card");
      card.innerHTML = `
        <h3>${ev.model}</h3>
        <p><b>Range:</b> ${ev.range}</p>
        <p><b>Price:</b> ${ev.price}</p>
        <p><b>Charging Time:</b> ${ev.charging_time}</p>`;
      container.appendChild(card);
    });

    /* ===== Simple Chatbot ===== */
    function sendMessage() {
      const input = document.getElementById("user-input").value.toLowerCase();
      const output = document.getElementById("chat-output");
      let reply = "";

      if (input.includes("best")) reply = "Tata Nexon EV is a popular and reliable choice!";
      else if (input.includes("charging")) reply = "Most EVs charge in about 1 hour with fast chargers.";
      else if (input.includes("price")) reply = "EV prices start around ₹14 Lakh and go higher for premium models.";
      else if (input.includes("available")) reply = "We currently have Tata Nexon EV, MG ZS EV, Hyundai Kona, and Mahindra XUV400.";
      else if (input.includes("range")) reply = "EV ranges vary between 300 to 460 km depending on model.";
      else if (input.includes("hello") || input.includes("hi")) reply = "Hello! Ask me about EVs, range, price, or charging details.";
      else reply = "I’m still learning! Try asking about EV models, price, or charging.";

      output.innerHTML += `<p><b>You:</b> ${input}</p><p><b>Bot:</b> ${reply}</p>`;
      document.getElementById("user-input").value = "";
      output.scrollTop = output.scrollHeight;
    }
  </script>

</body>
</html>
