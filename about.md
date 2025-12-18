---
layout: page
title: About Me
permalink: /about/
---

<div class="about-header">
  <div class="about-intro">
    <h1>Dieudonné Munganga</h1>
    <p class="location">📍 Cape Town, South Africa</p>
    <div class="contact-links">
      <a href="mailto:dieudonneishara@gmail.com" class="btn-small">📧 Email</a>
      <a href="https://www.linkedin.com/in/dieudonn%C3%A9-munganga-b01111b7/" class="btn-small">🔗 LinkedIn</a>
      <a href="https://github.com/monsieurpapa" class="btn-small">💻 GitHub</a>
      <span class="phone">📞 (+27 713 363 312)</span>
    </div>
  </div>
  <div class="about-image">
    <img src="{{site.baseurl}}/images/dieudo.jpeg" alt="Dieudonné Munganga" class="profile-pic">
  </div>
</div>

<div class="summary-section">
  <h3>Summary</h3>
  <p>Self-driven research engineer with an analytical and driven mindset. Dedicated to combining data and software engineering to craft socially impactful innovative solutions.</p>
</div>

<div class="skills-grid">
  <div class="skill-category">
    <h4>🛠️ Core Engineering</h4>
    <ul>
      <li><strong>Languages:</strong> Python, Java, JavaScript</li>
      <li><strong>Frameworks:</strong> Django, Flask, Bootstrap 5, SQLAlchemy</li>
      <li><strong>Web:</strong> RESTful APIs, GraphQL</li>
    </ul>
  </div>
  <div class="skill-category">
    <h4>☁️ Cloud & DevOps</h4>
    <ul>
      <li><strong>DevOps:</strong> Docker, Kubernetes, Git, GitHub Actions</li>
      <li><strong>Cloud:</strong> AWS, GCP, Heroku</li>
      <li><strong>Data Orchestration:</strong> Apache Airflow</li>
    </ul>
  </div>
  <div class="skill-category">
    <h4>📊 Data & Geospatial</h4>
    <ul>
      <li><strong>GIS:</strong> GIS Programming, GEE, Sentinel Hub</li>
      <li><strong>Databases:</strong> PostgreSQL, SQL, InfluxDB, Redis, MongoDB, AWS RDS</li>
    </ul>
  </div>
</div>

<hr>

### 💼 Professional Experience

#### **Consultant Research Engineer** | Dussoft Congo Sarl
*07/2024 — Current*
- Co-leading **Geospatial Data Analysis** for humanitarian crisis response.
- Designing and managing ETL processes for geospatial data from multiple sources (**GEE, Sentinel Hub, SAR**).
- Crafting and publishing reports that drive social impact innovation in humanitarian crisis-affected places.
- **Tech Stack:** Python, GCP, BigQuery, GIS, RESTful APIs, Git, Machine Learning, Airflow.

#### **Freelance Full Stack Assessor** | Code Institute
*06/2024 — Current*
- Assessing 2 full-stack projects daily to ensure compliance with industry best practices (UI/UX, Agile, Git, Clean Code, Testing, Secure Deployment).
- Providing structured, bias-free feedback on each SDLC phase of student projects.
- **Tech Stack:** Python, Django, Postgres, HTML, JavaScript (Bootstrap 5), Cloudinary, Heroku, Git.

#### **Software Engineer** | DevBoks
*01/2023 — 06/2024*
- Crafted **Micro-services based architecture** for SDN/SDWAN systems (up to 3 clusters, 10 pods/cluster).
- Established API-centered workflows to fuse 5 services of a Tier-1 network operator into one platform.
- Enhanced real-time network telemetry data pipelines, reducing database query delays by **up to 74%**.
- Led the SDLC for a NOS-agnostic training platform accommodating **350 simultaneous trainees**.

#### **Research Engineer** | AFRINIC
*07/2021 — 11/2021*
- Designed and maintained ETL data pipelines for the **'Measuring Internet Resilience in Africa' (MIRA)** project.
- Manipulated up to **2 million rows of data** across multiple cloud providers using SQL.
- Generated and presented monthly dashboards to key stakeholders.
- **Tech Stack:** Python, PyData, Shell Scripting, GCP (BigQuery, Data Studio), AWS, Balena, SQL.

#### **Research Engineer Intern** | AFRINIC
*08/2020 — 11/2020*
- Developed a **Telegram bot** to monitor 20 Raspberry Pi devices spread across 12 African countries.
- Automated daily reports on key data insights for stakeholders.
- Presented project updates at public online conferences.

<hr>

### 🎓 Education

*   **Master of Science: Computer Science** | University of Cape Town (2022)
*   **Bachelor of Science: Computer Science** | University of Cape Town (2020)
*   **Bachelor of Science: Computer Science** | Uganda Christian University (2017)

<hr>

### 🚀 Key Projects

*   **AgriSight:** Leveraging satellite imagery for crop health findings in conflict-affected regions.
*   **Network Training Platform:** NOS-agnostic platform for virtual router configurations. [manrs.dev.devboks.com](https://manrs.dev.devboks.com)
*   **Internet Performance (DRC):** Micro-service based measurement system influencing policy in the DR Congo.

<hr>

### 🗣️ Languages

*   **French:** Bilingual (C2) 🇫🇷
*   **English:** Advanced (C1) 🇬🇧

---

<style>
.about-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 30px;
  margin-bottom: 40px;
}
.about-intro h1 {
  margin-top: 0;
  font-size: 2.5rem;
}
.location {
  font-size: 1.1rem;
  color: var(--gray);
  margin: -10px 0 20px 0;
}
.contact-links {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  align-items: center;
}
.contact-links .btn-small {
  background: var(--lightGray);
  padding: 5px 12px;
  border-radius: 6px;
  font-size: 0.9rem;
  color: var(--darkGray);
  text-decoration: none;
  border: 1px solid var(--border-color);
  transition: all 0.2s ease;
}
.contact-links .btn-small:hover {
  background: var(--blue);
  color: white;
  border-color: var(--blue);
}
.phone {
  font-size: 0.9rem;
  color: var(--gray);
  margin-left: 5px;
}
.profile-pic {
  width: 180px;
  height: 180px;
  border-radius: 50%;
  object-fit: cover;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  border: 4px solid var(--white);
}
.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 20px;
  margin: 30px 0;
}
.skill-category {
  background: var(--lightGray);
  padding: 20px;
  border-radius: 10px;
  border: 1px solid var(--border-color);
}
.skill-category h4 {
  margin-top: 0;
  margin-bottom: 15px;
  border-bottom: 2px solid var(--blue);
  display: inline-block;
}
.skill-category ul {
  padding-left: 0;
  list-style: none;
  margin: 0;
}
.skill-category li {
  margin-bottom: 8px;
  font-size: 0.95rem;
}

@media (max-width: 640px) {
  .about-header {
    flex-direction: column-reverse;
    text-align: center;
  }
  .contact-links {
    justify-content: center;
  }
  .profile-pic {
    width: 150px;
    height: 150px;
  }
}
</style>
