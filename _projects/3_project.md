---
layout: page
title: Self-hosted AI
description: How can I self-host my own AI?
img: assets/img/7.jpg
importance: 4
category: work
---
## AI Agent Tutorial: A Dockerized Solution

Here are some tutorials:
Chatbot with pdf's [https://community.n8n.io/t/how-to-build-a-chat-with-your-document-chatbot-step-by-step-tutorial/39771]
### Tools Used
* **Llama 3.1:** A powerful language model for generating text, translating languages, writing different kinds of creative content, and answering your questions in an informative way.
* **n8n:** A flexible and extensible workflow automation tool that can be used to integrate various services and applications.
* **PostgreSQL:** A robust, open-source object-relational database system.
* **Docker:** A platform for packaging, distributing, and running applications in containers.

### Set Up

**1. Prerequisites:**
* Docker installed and running on your system.
* Basic understanding of Docker commands.

**2. Docker Compose File (docker-compose.yml):**

```yaml
version: '3.8'

services:
  llama:
    image: 'ai/llama-cpp:3.1'
    volumes:
      - ./models:/models
    ports:
      - '5000:5000'
    environment:
      - LLM_MODEL=your_model_file.bin
      - LLM_CONTEXT_SIZE=512
      - LLM_N_CTX_TOKENS=512
      - LLM_N_PREDICT_TOKENS=512

  n8n:
    image: 'n8n/n8n'
    ports:
      - '5678:5678'
    volumes:
      - ./n8n:/n8n
    environment:
      - N8N_PORT=5678
      - N8N_SUBDOMAIN=your_n8n_subdomain

  postgres:
    image: 'postgres:latest'
    environment:
      POSTGRES_PASSWORD: your_postgres_password
      POSTGRES_DB: your_postgres_database
      POSTGRES_USER: your_postgres_user
    ports:
      - '5432:5432'
```

**3. Build and Run:**
1. **Create necessary directories:**
   ```bash
   mkdir models n8n
   ```
2. **Download the Llama 3.1 model:**
   * Place the model file in the `models` directory.
3. **Configure n8n:**
   * Set up your desired workflows in n8n, including nodes for interacting with Llama, PostgreSQL, and other services.
4. **Start the services:**
   ```bash
   docker-compose up -d
   ```

### Testing
* **Access Llama:**
   * Use a tool like `curl` or a web interface to send requests to the Llama API.
* **Test n8n Workflows:**
   * Trigger your workflows and verify that they interact correctly with Llama, PostgreSQL, and other services.
* **Query PostgreSQL:**
   * Use a database client like `pgAdmin` or `psql` to connect to the PostgreSQL database and query the data.

### Results
By following these steps, you should have a fully functional AI agent setup, leveraging the power of Llama 3.1, n8n, and PostgreSQL, all containerized with Docker. This provides a flexible and scalable solution for various AI-powered applications.

**Additional Considerations:**
* **Security:** Implement appropriate security measures, such as strong passwords, network segmentation, and regular security updates.
* **Performance:** Optimize your Docker Compose file and container configurations for optimal performance.
* **Monitoring:** Use tools like `Docker Stats` and `n8n Monitoring` to monitor the health and performance of your services.
* **Scaling:** Consider using Docker Swarm or Kubernetes for scaling your application.

**Remember to replace placeholders like `your_model_file.bin`, `your_n8n_subdomain`, and PostgreSQL credentials with your actual values.**

    <!-- ---
    layout: page
    title: project
    description: a project with a background image
    img: /assets/img/12.jpg
    ---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/1.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/3.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Caption photos easily. On the left, a road goes through a tunnel. Middle, leaves artistically fall in a hipster photoshoot. Right, in another hipster photoshoot, a lumberjack grasps a handful of pine needles.
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

You can also put regular text between your rows of images.
Say you wanted to write a little bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, _bled_ for your project, and then... you reveal its glory in the next row of images.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>

The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}

```html
<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
```

{% endraw %} -->
