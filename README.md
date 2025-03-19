<<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Sumit Singha | Portfolio</title>
  <style>
    /* Reset & Smooth Scrolling */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    html {
      scroll-behavior: smooth;
    }
    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
      background: #1E1E1E; /* Dark grey background */
      color: #e0e0e0; /* Light text */
      overflow-x: hidden;
    }
    
    /* Fixed Navigation */
    nav {
      position: fixed;
      top: 0;
      width: 100%;
      background: #343541; /* Dark grey */
      padding: 15px 0;
      z-index: 100;
      display: flex;
      justify-content: center;
      transition: background 0.3s ease;
    }
    nav a {
      color: #e0e0e0;
      text-decoration: none;
      padding: 0 20px;
      font-size: 1em;
      transition: color 0.3s;
    }
    nav a:hover {
      color: #B0B3B8;
    }
    
    /* Hero Header Section */
    header {
      position: relative;
      width: 100%;
      height: 100vh;
      background: url('https://www.apple.com/v/iphone/home/au/images/overview/hero/hero_iphone__b6viqzjbzci2_large.jpg') no-repeat center center/cover;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      color: white;
      overflow: hidden;
    }
    /* A semi-transparent overlay (optional) */
    header::before {
      content: "";
      position: absolute;
      top: 0; 
      left: 0;
      width: 100%; 
      height: 100%;
      background: linear-gradient(135deg, rgba(52,53,65,0.6), rgba(52,53,65,0.3));
      z-index: 1;
    }
    /* Background image behind header text using an actual image tag */
    .header-bg {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 0;
    }
    .header-bg img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      opacity: 0.15; /* Lower opacity so it doesn't overwhelm the text */
    }
    .header-content {
      position: relative;
      z-index: 2;
      padding: 20px;
      animation: fadeInUp 1s ease-out;
    }
    .header-content h1 {
      font-size: 4em;
      margin-bottom: 20px;
      letter-spacing: 2px;
    }
    .header-content p {
      font-size: 1.5em;
      font-weight: 300;
    }
    @keyframes fadeInUp {
      from {
        opacity: 0;
        transform: translateY(20px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    
    /* Main Container & Section Animations */
    .container {
      padding: 100px 10% 80px; /* extra top padding to account for fixed nav */
    }
    .section {
      margin-bottom: 100px;
      opacity: 0;
      transform: translateY(30px);
      transition: all 0.6s ease-out;
    }
    .section.in-view {
      opacity: 1;
      transform: translateY(0);
    }
    .section h2 {
      font-size: 2.5em;
      margin-bottom: 20px;
      border-bottom: 2px solid #B0B3B8;
      padding-bottom: 10px;
      color: #e0e0e0;
    }
    
    /* About Section */
    #about {
      text-align: center;
    }
    .profile-picture {
      width: 200px;
      height: 200px;
      border-radius: 50%;
      object-fit: cover;
      margin: 20px auto;
      border: 5px solid #343541;
      box-shadow: 0 0 20px rgba(60,64,67,0.4);
      transition: box-shadow 0.3s ease;
    }
    .profile-picture:hover {
      box-shadow: 0 0 30px rgba(60,64,67,0.6);
    }
    
    /* Professional Experience Section (Accordion-Style) */
    .experience {
      background-color: #2C2F33; /* Dark grey card */
      box-shadow: 0 8px 16px rgba(60,64,67,0.4);
      border-radius: 15px;
      margin-bottom: 50px;
      cursor: pointer;
      overflow: hidden;
      max-height: 90px;
      transition: max-height 0.5s ease, transform 0.3s ease, box-shadow 0.3s ease;
    }
    .experience:hover {
      transform: scale(1.02);
      box-shadow: 0 0 20px rgba(60,64,67,0.6);
      max-height: 1000px;
    }
    .experience-content {
      padding: 20px;
    }
    .experience-content h3 {
      font-size: 1.8em;
      margin-bottom: 10px;
      color: #e0e0e0;
    }
    .experience-content p {
      font-size: 1em;
      color: #B0B3B8;
    }
    /* Hidden details that expand on hover */
    .details {
      opacity: 0;
      max-height: 0;
      overflow: hidden;
      transition: opacity 0.5s ease, max-height 0.5s ease;
      margin-top: 10px;
    }
    .experience:hover .details {
      opacity: 1;
      max-height: 1000px;
    }
    .details ul {
      list-style-type: disc;
      padding-left: 20px;
      font-size: 1em;
      color: #e0e0e0;
      margin-top: 10px;
    }
    
    /* Skills Section */
    .skills-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 20px;
    }
    .skill {
      background: #2C2F33; /* Dark grey card */
      border: 1px solid #444;
      border-radius: 10px;
      padding: 20px;
      text-align: center;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      cursor: default;
      color: #e0e0e0;
    }
    .skill:hover {
      transform: scale(1.05);
      box-shadow: 0 0 10px rgba(60,64,67,0.4);
    }
    .skill h4 {
      font-size: 1.2em;
      margin-bottom: 10px;
    }
    
    /* Contact Section */
    #contact {
      text-align: center;
    }
    #contact a {
      color: #e0e0e0;
      font-weight: bold;
      text-decoration: none;
      border-bottom: 2px solid transparent;
      transition: border-bottom 0.3s;
    }
    #contact a:hover {
      border-bottom: 2px solid #e0e0e0;
    }
    
    /* Footer */
    footer {
      background: #343541;
      color: #e0e0e0;
      text-align: center;
      padding: 20px;
      font-size: 0.9em;
    }
  </style>
</head>
<body>

  <!-- Fixed Navigation -->
  <nav>
    <a href="#about">About</a>
    <a href="#experience">Experience</a>
    <a href="#skills">Skills</a>
    <a href="#contact">Contact</a>
  </nav>

  <!-- Hero Header -->
  <header>
    <!-- Background Image using an img tag -->
    <div class="header-bg" style="position:absolute; top:0; left:0; width:100%; height:100%; z-index:0;">
      <img src="/image/Sumit background.jpeg" alt="Background" style="width:100%; height:100%; object-fit:cover; opacity:0.15;">
    </div>
    <div class="header-content">
      <h1>Sumit Singha</h1>
      <p>Innovate. Create. Inspire.</p>
    </div>
  </header>

  <!-- Main Container -->
  <div class="container">
    
    <!-- About Section -->
    <section class="section" id="about">
      <h2>About Me</h2>
      <img src="/image/Sumit Singha.jpg" alt="Sumit Singha" class="profile-picture">
      <p>
        Passionate creator and entrepreneur with extensive experience in digital marketing, brand development, 
        and innovative project management. Always striving to bring creative solutions to life and inspire 
        those around me.
      </p>
    </section>
    
    <!-- Professional Experience Section -->
    <section class="section" id="experience">
      <h2>Professional Experience</h2>
      
      <!-- Experience Card 1: Special Advisor -->
      <div class="experience" style="display: flex; align-items: flex-start;">
        <div class="experience-content" style="flex: 1;">
          <h3>Special Advisor to the Secretary General – PR & Communications</h3>
          <p>Legatio 23 Model United Nations | Siliguri, West Bengal, India | 04/2023 – 11/2023</p>
          <div class="details">
            <ul>
              <li><strong>Strategic Leadership:</strong> Managed public relations and communications, fostering diverse delegate engagement.</li>
              <li><strong>Innovative Marketing:</strong> Boosted event reach and engagement through creative social media campaigns.</li>
              <li><strong>Effective Communication:</strong> Streamlined information flow between secretariat, delegates, and stakeholders.</li>
              <li><strong>Crisis Management:</strong> Resolved challenges efficiently, safeguarding the organization’s reputation.</li>
              <li><strong>Promotional Success:</strong> Implemented targeted digital strategies, increasing participation and global visibility.</li>
            </ul>
          </div>
        </div>
        <div class="experience-image" style="margin-left: 20px;">
          <img src="/image/Special Advisor.jpeg" alt="Special Advisor Image" style="width:300px; border-radius:10px;">
        </div>
      </div>
      
      <!-- Experience Card 2: Office Student Assistant -->
      <div class="experience">
        <div class="experience-content">
          <h3>Office Student Assistant – HRL Front Desk</h3>
          <p>Wichita State University | 01/2024</p>
          <div class="details">
            <ul>
              <li><strong>Streamlined Operations:</strong> Enhanced productivity by optimizing scheduling, correspondence, and file management.</li>
              <li><strong>Tech-Savvy:</strong> Proficient in Microsoft Office Suite and student database systems for smooth operations.</li>
              <li><strong>Student Liaison:</strong> Improved communication between students and faculty, resolving academic inquiries.</li>
              <li><strong>Event Leadership:</strong> Coordinated campus events, increasing student participation through strategic planning.</li>
              <li><strong>Data Accuracy:</strong> Maintained precise records and prepared insightful reports for informed decision-making.</li>
            </ul>
          </div>
        </div>
      </div>
      
      <!-- Experience Card 3: AI Research Developer Team Leader -->
      <div class="experience">
        <div class="experience-content">
          <h3>AI Research Developer Team Leader – Innovation Campus</h3>
          <p>Wichita State University | 01/2025 – Present</p>
          <div class="details">
            <ul>
              <li><strong>AI Chatbot Development:</strong> Conceptualized and implemented an AI chatbot for WSU’s website using LLM, RAG, HTML, Java, and C++.</li>
              <li><strong>Tool Research & Workflow Optimization:</strong> Researched 20+ AI tools (PowerPoint, image generation, CRMs, etc.) to streamline operations.</li>
              <li><strong>Marketing Automation:</strong> Enhanced prompt engineering for dynamic newsletters and emails, supporting AI-driven content creation.</li>
              <li><strong>Immersive Workflow Innovation:</strong> Explored cutting-edge AI tools to seamlessly integrate technology into workforce development.</li>
              <li><strong>Technical Documentation:</strong> Compiled comprehensive reports on AI tool capabilities, providing actionable insights for strategic advancements.</li>
            </ul>
          </div>
        </div>
      </div>

      <!-- Experience Card 4: AI Chatbot for Wichita State University -->
      <div class="experience">
        <div class="experience-content">
          <h3>AI Chatbot for Wichita State University</h3>
          <p>01/2025 – Present</p>
          <div class="details">
            <ul>
              <li><strong>Intelligent Assistant:</strong> Designed to streamline university communications and provide real-time answers to students.</li>
              <li><strong>Live Demo:</strong> <a href="https://langflow-ai-chatbot-server.onrender.com/" target="_blank" style="color:#B0B3B8;">Try the AI Chatbot</a></li>
            </ul>
          </div>
          <!-- Additional content: Image and WSU Profile Link -->
          <div class="experience-additional">
            <img src="/image/Sumit wsu page.jpeg" alt="WSU AI Chatbot" style="width:100%; border-radius:10px; margin-top:15px;">
            <p style="margin-top: 10px;">
              <a href="https://www.wichita.edu/profiles/research/TIE_Team_Members/03_AI_research_and_development/01_Singha-Sumit.php" target="_blank" style="color:#B0B3B8;">View My WSU Profile</a>
            </p>
          </div>
        </div>
      </div>
      
      <!-- Experience Card 5: Technology Industry Engagement (TIE) -->
      <div class="experience">
        <div class="experience-content">
          <h3>Technology Industry Engagement (TIE)</h3>
          <p style="margin-bottom: 10px;">
            I am deeply grateful to <a href="https://www.linkedin.com/in/tonyawitherspoon/" target="_blank" style="color:inherit; text-decoration:underline;">Tonya Witherspoon</a>, <a href="https://www.linkedin.com/in/brendanjmcdonough/" target="_blank" style="color:inherit; text-decoration:underline;">Brendan McDonough</a>, and <a href="https://www.linkedin.com/in/samoeding/" target="_blank" style="color:inherit; text-decoration:underline;">Samuel Oeding</a> for recruiting me into this department and providing me with an incredible opportunity to grow professionally.
          </p>
          <p>Wichita State University</p>
          <img src="/image/TIE.jpeg" alt="TIE Department Group Photo" style="width:100%; border-radius:10px; margin-bottom:15px;">
          <div class="details">
            <ul>
              <li><strong>Driving Innovation:</strong> Fostering partnerships through hands-on student engagement at Wichita State University.</li>
              <li><strong>Collaboration Focus:</strong> Bridges students and businesses, providing applied learning experiences for real-world challenges.</li>
            </ul>
          </div>
        </div>
      </div>
      
    </section>
    
    <!-- Skills Section -->
    <section class="section" id="skills">
      <h2>Skills</h2>
      <div class="skills-grid">
        <div class="skill">
          <h4>Leadership & Advisory</h4>
        </div>
        <div class="skill">
          <h4>Interpersonal & Communication</h4>
        </div>
        <div class="skill">
          <h4>Data Management & Reporting</h4>
        </div>
        <div class="skill">
          <h4>Java</h4>
        </div>
        <div class="skill">
          <h4>C++</h4>
        </div>
        <div class="skill">
          <h4>Business Analysis</h4>
        </div>
        <div class="skill">
          <h4>HTML, CSS, JavaScript</h4>
        </div>
        <div class="skill">
          <h4>Project Management</h4>
        </div>
        <div class="skill">
          <h4>Adaptability</h4>
        </div>
        <div class="skill">
          <h4>Microsoft Power BI</h4>
        </div>
        <div class="skill">
          <h4>Prompt Engineering</h4>
        </div>
        <div class="skill">
          <h4>SQL & Database Knowledge</h4>
        </div>
        <div class="skill">
          <h4>LLMOps</h4>
        </div>
        <div class="skill">
          <h4>RAG</h4>
        </div>
        <div class="skill">
          <h4>Technical Documentation</h4>
        </div>
        <div class="skill">
          <h4>Testing Procedures</h4>
        </div>
        <div class="skill">
          <h4>Software Frameworks</h4>
        </div>
      </div>
    </section>
    
    <!-- Contact Section -->
    <section class="section" id="contact">
      <h2>Get In Touch</h2>
      <p>Email: <a href="mailto:sxsingha@shockers.wichita.edu">sxsingha@shockers.wichita.edu</a></p>
      <p>LinkedIn: <a href="https://www.linkedin.com/in/sumit-singha-b88554295/" target="_blank">Sumit Singha</a></p>
    </section>
  </div>

  <!-- Footer -->
  <footer>
    &copy; 2025 Sumit Singha. All rights reserved.
  </footer>

  <!-- JavaScript for Scroll-Triggered Animations -->
  <script>
    document.addEventListener('DOMContentLoaded', function() {
      const sections = document.querySelectorAll('.section');
      const options = { threshold: 0.2 };
      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.classList.add('in-view');
          }
        });
      }, options);
      sections.forEach(section => observer.observe(section));
    });
  </script>
</body>
</html>
