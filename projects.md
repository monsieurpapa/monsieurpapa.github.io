---
layout: page
title: Projects
permalink: /projects/
---

Explore my recent work across Software Engineering, Data Engineering, and ICT4D. These projects range from microservices architectures to AI-powered research tools.

<div class="projects-grid">
  
  <div class="project-card">
    <div class="project-image" style="background-image: url('{{site.baseurl}}/images/agricultural_stress_simulation.jpeg')"></div>
    <div class="project-content">
      <h3>AgriSight</h3>
      <p>Microservices platform for agricultural stress detection using Sentinel-2 satellite data and Machine Learning.</p>
      <div class="project-tags">
        <span>Python</span><span>React</span><span>PostGIS</span><span>ML</span>
      </div>
      <a href="{{site.baseurl}}/AgriSight-Monitoring/" class="btn">View Case Study</a>
    </div>
  </div>

  <div class="project-card">
    <div class="project-image" style="background-image: url('{{site.baseurl}}/images/intercon.png')"></div>
    <div class="project-content">
      <h3>BeansPath</h3>
      <p>Traceability platform for coffee and cocoa supply chains with AI-powered insights for farmers.</p>
      <div class="project-tags">
        <span>TypeScript</span><span>PostgreSQL</span><span>AI</span><span>Docker</span>
      </div>
      <a href="{{site.baseurl}}/BeansPath-Traceability/" class="btn">View Case Study</a>
    </div>
  </div>

  <div class="project-card">
    <div class="project-image" style="background-image: url('{{site.baseurl}}/images/404.jpg')"></div>
    <div class="project-content">
      <h3>KivuSafe</h3>
      <p>Privacy-first community safety platform for incident reporting and safe route navigation.</p>
      <div class="project-tags">
        <span>Next.js</span><span>Prisma</span><span>Security</span><span>PWA</span>
      </div>
      <a href="{{site.baseurl}}/KivuSafe-Security/" class="btn">View Case Study</a>
    </div>
  </div>

  <div class="project-card">
    <div class="project-image" style="background-image: url('{{site.baseurl}}/images/step1.gif')"></div>
    <div class="project-content">
      <h3>TicketNavigator</h3>
      <p>Digital booking system for boat transport on Lake Kivu, including QR-ticketing and fleet management.</p>
      <div class="project-tags">
        <span>Node.js</span><span>React</span><span>PostgreSQL</span>
      </div>
      <a href="{{site.baseurl}}/TicketNavigator-Booking/" class="btn">View Case Study</a>
    </div>
  </div>

  <div class="project-card">
    <div class="project-image" style="background-image: url('{{site.baseurl}}/images/config.png')"></div>
    <div class="project-content">
      <h3>Network Training Platform</h3>
      <p>A NOS-agnostic platform allowing trainees to apply configurations to virtual routers via the Web using Containerlab and microservices.</p>
      <div class="project-tags">
        <span>Docker</span><span>Django</span><span>Containerlab</span><span>AWS</span>
      </div>
      <a href="https://manrs.dev.devboks.com" class="btn">Visit Platform</a>
    </div>
  </div>

  <div class="project-card">
    <div class="project-image" style="background-image: url('{{site.baseurl}}/images/internetmeasurement.jpg')"></div>
    <div class="project-content">
      <h3>Internet Performance (DRC)</h3>
      <p>Deployment of a micro-service system on Raspberry Pis to measure QoS and QoE, influencing policy and industry decisions in the DRC.</p>
      <div class="project-tags">
        <span>Python</span><span>Raspberry Pi</span><span>GCP</span><span>BigQuery</span>
      </div>
      <a href="{{site.baseurl}}/recherche/" class="btn">View Research</a>
    </div>
  </div>

  <div class="project-card">
    <div class="project-image" style="background-image: url('{{site.baseurl}}/images/config.png')"></div>
    <div class="project-content">
      <h3>Permit Management</h3>
      <p>Enterprise RBAC system for automating regulatory permit compliance and audit trails.</p>
      <div class="project-tags">
        <span>Django</span><span>Celery</span><span>Redis</span><span>DevOps</span>
      </div>
      <a href="{{site.baseurl}}/Permit-Management/" class="btn">View Case Study</a>
    </div>
  </div>

</div>

<style>
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 30px;
  margin-top: 40px;
}

.project-card {
  background: var(--white);
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
  transition: transform 0.3s ease, box-shadow 0.3s ease, background-color 0.3s ease, border-color 0.3s ease;
  border: 1px solid var(--border-color);
  display: flex;
  flex-direction: column;
}

.project-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
}

.project-image {
  height: 180px;
  background-size: cover;
  background-position: center;
  border-bottom: 1px solid var(--border-color);
}

.project-content {
  padding: 20px;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
}

.project-content h3 {
  margin: 0 0 10px 0;
  font-size: 1.25rem;
  color: var(--black);
}

.project-content p {
  font-size: 0.95rem;
  color: var(--gray);
  margin-bottom: 15px;
  line-height: 1.5;
  flex-grow: 1;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 20px;
}

.project-tags span {
  background: var(--lightGray);
  color: var(--gray);
  padding: 4px 10px;
  border-radius: 20px;
  font-size: 0.75rem;
  font-weight: 600;
}

.project-content .btn {
  display: inline-block;
  background: var(--blue);
  color: #fff !important;
  padding: 10px 20px;
  border-radius: 6px;
  text-decoration: none;
  font-weight: 600;
  font-size: 0.9rem;
  text-align: center;
  transition: background 0.2s;
}

.project-content .btn:hover {
  background: var(--hover-blue);
  text-decoration: none;
}
</style>
