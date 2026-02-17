# 🚀 Automating a Full Microservices Architecture with Ansible  
## My Roboshop Infrastructure Automation Journey

There was a time when deploying an application meant:

- SSH into the server  
- Install Node.js / Python / Java  
- Configure databases  
- Create users  
- Copy service files  
- Restart systemd  
- Debug logs manually  

It worked.

But only for one server.

---

## 🧠 The Real Question

I asked myself:

> If I can deploy one service manually, can I deploy the entire microservices architecture the same way every time?

What about:

- 20+ servers?
- Multiple environments (Dev / QA / Prod)?
- Zero configuration drift?
- Safe re-runs without breaking production?

That’s when I stopped thinking like a “Linux user”  
And started thinking like a **Platform Engineer**.

---

# 🛒 The Application: Roboshop

Roboshop is a full-stack microservices e-commerce platform.

It includes:

### 🧩 Backend Services
- Catalogue (Node.js)
- Cart (Node.js)
- User (Node.js)
- Shipping (Java)
- Payment (Python)

### 🗄 Data Layer
- MongoDB
- MySQL

### ⚡ Supporting Infrastructure
- Redis (Caching)
- RabbitMQ (Messaging)
- Nginx (Frontend)

Multiple services.  
Multiple dependencies.  
Inter-service communication.  

Perfect real-world automation challenge.

---

# ⚙️ What This Automation Solves

Instead of manually configuring everything, this Ansible project handles:

- Package installation
- Runtime setup (Node.js, Python, Java)
- User and directory creation
- Application artifact deployment
- Dependency installation (npm, pip, maven)
- systemd service configuration
- Environment variable templating (Jinja2)
- Service enable & restart
- Health verification

Everything runs in a consistent, repeatable, idempotent way.

---

# 🧪 Real Debugging Moment

During the Catalogue service deployment, the health endpoint returned:

```
"mongo": false
```

The issue?

The `MONGODB_HOST` variable was not rendered properly in the systemd unit file.

After fixing the Jinja template and reloading systemd:

```
"mongo": true
```

That moment reinforced something important:

Automation is not about running commands.  
It’s about defining the correct desired state.

---

# 🔁 Why Ansible?

- Agentless (SSH-based)
- Push model
- Simple YAML syntax
- Idempotent execution
- Easy environment grouping via inventory

It allows infrastructure to be described — not manually built.

---

# 🚀 How to Run

```bash
git clone https://github.com/NagaAjay1812/ansible-roboshop
cd ansible-roboshop
ansible-playbook -i inventory.ini roboshop.yaml
```

One command.

Entire microservices architecture deployed.

---

# 📌 Key Learnings

- Idempotent automation design
- Service dependency orchestration
- Infrastructure consistency across environments
- Debugging via structured configuration management
- Thinking in systems, not servers

---

## 🎯 Final Thought

Linux gives control.  
Automation gives consistency.  

This project helped me transition from executing commands  
to designing reliable infrastructure systems.
