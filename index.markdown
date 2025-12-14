---
layout: main
title: Home
permalink: /
---


<section id="bio" class="section section-bio">
  <div class="container section-inner flex-row">
    <div class="bio-left">
      <!-- Headshot -->
      <img class="headshot" src="{{ '/assets/images/headshot.jpg' | relative_url }}" alt="Headshot of Your Name">

      <!-- Social icons -->
      <div class="social-icons">
        <!-- GitHub -->
        <a href="{{ site.social.github }}" aria-label="GitHub" class="icon">
          <!-- inline GitHub SVG -->
          <svg viewBox="0 0 24 24" width="20" height="20" aria-hidden="true"><path d="M12 .5C5.73.5.75 5.48.75 11.77c0 4.93 3.19 9.11 7.61 10.58.56.1.76-.24.76-.53 0-.26-.01-.95-.01-1.86-3.09.67-3.74-1.49-3.74-1.49-.51-1.3-1.25-1.65-1.25-1.65-1.02-.7.08-.69.08-.69 1.12.08 1.71 1.15 1.71 1.15 1.01 1.73 2.65 1.23 3.3.94.1-.73.39-1.23.71-1.51-2.47-.28-5.07-1.24-5.07-5.52 0-1.22.43-2.22 1.14-3-.11-.28-.5-1.42.11-2.96 0 0 .93-.3 3.05 1.14.89-.25 1.85-.38 2.8-.38.95 0 1.91.13 2.8.38 2.12-1.44 3.05-1.14 3.05-1.14.61 1.54.22 2.68.11 2.96.71.78 1.14 1.78 1.14 3 0 4.29-2.61 5.24-5.09 5.52.4.34.76 1.01.76 2.04 0 1.47-.01 2.66-.01 3.02 0 .29.2.64.77.53 4.42-1.47 7.61-5.65 7.61-10.58C23.25 5.48 18.27.5 12 .5z"/></svg>
        </a>

        <!-- LinkedIn -->
        <a href="{{ site.social.linkedin }}" aria-label="LinkedIn" class="icon">
          <svg viewBox="0 0 24 24" width="20" height="20" aria-hidden="true"><path d="M4.98 3.5C3.88 3.5 3 4.38 3 5.5s.88 2 1.98 2h.02C6.08 7.5 7 6.62 7 5.5S6.08 3.5 4.98 3.5zM3.5 8.98H6.5V21H3.5zM9.5 8.98h2.86v1.62h.04c.4-.75 1.37-1.62 2.82-1.62 3.02 0 3.58 1.99 3.58 4.58V21h-3V14.5c0-1.53-.03-3.5-2.14-3.5-2.14 0-2.47 1.66-2.47 3.38V21h-3z"/></svg>
        </a>

        <!-- Email -->
        <a href="mailto:your.email@example.com" aria-label="Email" class="icon">
          <svg viewBox="0 0 24 24" width="20" height="20" aria-hidden="true"><path d="M20 4H4c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4-8 5-8-5V6l8 5 8-5v2z"/></svg>
        </a>
      </div>

      <!-- downloads -->
      <div class="downloads">
        <a class="button" href="{{ '/assets/files/resume.pdf' | relative_url }}" download>Download Resume</a>
        <a class="button" href="{{ '/assets/files/cv.pdf' | relative_url }}" download>Download CV</a>
      </div>

    </div>

    <div class="bio-right">
      <h2>Your Name</h2>
      <p class="bio-text">
        <!-- Replace with your biography -->
        I'm a robotics researcher focusing on motion planning, navigation, and swarm systems. My work spans theory and real-world systems, with an emphasis on safe autonomy and human-robot interaction. Replace this paragraph with your full biography.
      </p>

      <ul class="bio-highlights">
        <li>Ph.D. in Robotics, University Name</li>
        <li>Focus: motion planning, swarm robotics, haptics</li>
        <li>Contact: your.email@example.com</li>
      </ul>
    </div>
  </div>
</section>

<section id="publications" class="section section-alt">
  <div class="container section-inner">
    <h2 class="section-title">Publications</h2>

    {% for pub in site.data.publications %}
      <article class="media-row {% if forloop.index0 | modulo:2 == 1 %}media-reverse{% endif %}">
        <div class="media-left">
          {% if pub.video %}
            <!-- Embed a video (YouTube) -->
            <div class="media-embed">
              <iframe src="{{ pub.video }}" frameborder="0" allowfullscreen title="{{ pub.title }}"></iframe>
            </div>
          {% else %}
            <img src="{{ pub.image | relative_url }}" alt="{{ pub.title }}">
          {% endif %}
        </div>

        <div class="media-right">
          <h3>{{ pub.title }}</h3>
          <p class="meta">{{ pub.authors }} — <em>{{ pub.venue }}</em> ({{ pub.year }})</p>
          <p>{{ pub.description }}</p>
          {% if pub.link %}
            <p><a class="link" href="{{ pub.link }}">Read / Watch</a></p>
          {% endif %}
        </div>
      </article>
    {% endfor %}
  </div>
</section>

<section id="projects" class="section section-bio">
  <div class="container section-inner">
    <h2 class="section-title">Projects</h2>

    {% for proj in site.data.projects %}
      <article class="media-row {% if forloop.index0 | modulo:2 == 1 %}media-reverse{% endif %}">
        <div class="media-left">
          {% if proj.video %}
            <div class="media-embed">
              <iframe src="{{ proj.video }}" frameborder="0" allowfullscreen title="{{ proj.title }}"></iframe>
            </div>
          {% else %}
            <img src="{{ proj.image | relative_url }}" alt="{{ proj.title }}">
          {% endif %}
        </div>

        <div class="media-right">
          <h3>{{ proj.title }}</h3>
          <p class="meta">{{ proj.short }}</p>
          <p>{{ proj.description }}</p>
          {% if proj.link %}
            <p><a class="link" href="{{ proj.link }}">Project page / code</a></p>
          {% endif %}
        </div>
      </article>
    {% endfor %}
  </div>
</section>

