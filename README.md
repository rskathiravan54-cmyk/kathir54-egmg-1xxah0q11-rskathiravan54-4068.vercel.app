<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>College Chatbot</title>

  <style>
    body {
      font-family: Arial, sans-serif;
      background: #eef3fb;
      margin: 0;
      padding: 20px;
    }

    .chatbox {
      max-width: 600px;
      margin: 30px auto;
      background: white;
      padding: 20px;
      border-radius: 15px;
    }

    h2 {
      text-align: center;
      color: #123c78;
    }

    #messages {
      height: 350px;
      overflow-y: auto;
      border: 1px solid #ddd;
      padding: 10px;
      border-radius: 10px;
    }

    .message {
      padding: 12px;
      margin: 10px 0;
      border-radius: 10px;
      white-space: pre-wrap;
    }

    .bot {
      background: #e7efff;
    }

    .user {
      background: #123c78;
      color: white;
      text-align: right;
    }

    .input-area {
      display: flex;
      gap: 8px;
      margin-top: 15px;
    }

    input {
      flex: 1;
      min-width: 0;
      padding: 12px;
      border: 1px solid #ccc;
      border-radius: 8px;
    }

    button {
      padding: 12px;
      background: #123c78;
      color: white;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }
  </style>
</head>

<body>

  <div class="chatbox">
    <h2>Thamirabharani Engineering College</h2>
    <p>College Information Chatbot</p>

    <div id="messages">
      <div class="message bot">
        Vanakkam! Welcome to Thamirabharani Engineering College.
        College pathi enna information venum?
      </div>
    </div>

    <div class="input-area">
      <input id="userInput"
             placeholder="Type your question..."
             onkeydown="if(event.key==='Enter') sendMessage()">

      <button onclick="sendMessage()">Send</button>
    </div>
  </div>

  <script>
    const college = {
      about: "Thamirabharani Engineering College. Located at Thachanallur, Tirunelveli.",

      departments: "Sample departments:\n1. AI & DS\n2. CSE\n3. ECE\n4. EEE\n5. Mechanical Engineering\n6. Civil Engineering. Please verify actual departments.",

      hostel: "Hostel details: Room facilities, food, study hall and security. Availability and fees need to be verified.",

      transport: "Transport details: College bus service, pickup and drop-off. Routes, timings and fees need to be verified.",

      sports: "Sports: Cricket, Volleyball, Football, Basketball, Chess, Table Tennis and Carrom. Please verify actual facilities."
    };

    function getReply(question) {
      const q = question.toLowerCase();

      if (q.includes("department") || q.includes("branch"))
        return college.departments;

      if (q.includes("hostel"))
        return college.hostel;

      if (q.includes("transport") || q.includes("bus"))
        return college.transport;

      if (q.includes("sport") || q.includes("game") ||
          q.includes("cricket"))
        return college.sports;

      if (q.includes("about") || q.includes("college") ||
          q.includes("name"))
        return college.about;

      return "Sorry! Indha question-ku answer en data-la illa. College, departments, hostel, transport, sports pathi kelunga.";
    }

    function addMessage(text, sender) {
      const messages = document.getElementById("messages");
      const div = document.createElement("div");

      div.className = "message " + sender;
      div.textContent = text;

      messages.appendChild(div);
      messages.scrollTop = messages.scrollHeight;
    }

    function sendMessage() {
      const input = document.getElementById("userInput");
      const question = input.value.trim();

      if (!question) return;

      addMessage(question, "user");
      input.value = "";

      const reply = getReply(question);
      addMessage(reply, "bot");
    }
  </script>

</body>
</html>
