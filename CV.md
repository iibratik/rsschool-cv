# Ibrat Ibragimov

![Photo](./profile_photo.jpg.jpg) <!-- Upload your professional photo -->

**Full-Stack Developer | JavaScript & Python**

---

## 📋 Contact Information

| Info | Value |
|-----------|-------|
| **Phone** | +998 77 293 11 25 |
| **Email** | iibratik17@gmail.com |
| **GitHub** | [github.com/iibratik](https://github.com/iibratik) |
| **LinkedIn** | [linkedin.com/in/iibratik](https://linkedin.com/in/iibratik) |
| **Discord** | zeref9011 |
| **Location** | Tashkent, Uzbekistan |

---

## 👤 About Me

I am a Full-Stack Developer with hands-on experience building web applications and business automation systems. My primary focus is transforming manual business processes into reliable, scalable automated workflows.

### My Goals and Priorities:
- Deepen expertise in modern frameworks (React, Vue.js, Next.js, Nuxt.js)
- Develop skills in microservices architecture and cloud deployment
- Gain international experience working in collaborative teams
- Specialize in building high-load, scalable systems
- Relocate to a European country and contribute to innovative tech projects

### My Strengths:
- **Fast Learner**: Ability to quickly master new technologies and tools
- **Process Automation**: Expert in converting manual workflows into automated solutions (Telegram bots, scripts)
- **System Integration**: Professional experience with REST APIs, webhooks, and ERP integrations
- **Problem Solving**: Comprehensive approach to diagnosing and resolving complex technical issues
- **Cross-functional Collaboration**: Successful collaboration across development, support, and business teams

### Work Experience:
- **Software Integration Specialist** at Watson DJ (March–July 2026) — MoySklad ERP configuration and integration development
- **Technical Support Specialist (L3)** at Terranova Software (May 2024 – February 2025) — technical support and software implementation
- **Freelance Web Developer** — WordPress/WooCommerce stores and web applications

### Commitment to Learning:
I actively improve my skills through practical projects and continuous education. Completed Claude Platform 101 course in 2026. Passionate about exploring emerging technologies, testing methodologies, and performance optimization.

---

## 🛠️ Technical Skills

### Programming Languages
- **JavaScript** — primary language, used in 80% of my projects
- **TypeScript** — strong typing in enterprise applications
- **Python** — automation, scripting, data processing (pandas)

### Frontend Frameworks and Libraries
- **Vue.js** — component architecture, state management (Pinia/Vuex)
- **React.js** — hooks, functional components, JSX patterns
- **Next.js** — SSR, API routes, performance optimization
- **Nuxt.js** — full-featured Vue.js meta-framework
- **HTML5 / CSS3** — semantic markup, flexbox, CSS Grid, responsive design

### Backend and API Development
- **Node.js** — REST API development, async/await patterns
- **Express.js / Fastify** — lightweight backend frameworks
- **REST API** — design, integration, documentation, best practices
- **WebHooks** — event handling, system integration

### Databases
- **PostgreSQL** — relational databases, complex queries, optimization
- **MS SQL Server** — enterprise environment experience
- **SQLite** — embedded databases for client applications

### Automation and Bots
- **Telegram Bot API** — bot development with aiogram and Telegraf
- **Web Scraping** — data parsing and collection
- **Data Migration** — pandas, migration scripts, data transformation
- **APScheduler** — task scheduling and execution

### E-commerce and CMS
- **WordPress** — setup, customization, plugin management
- **WooCommerce** — e-commerce store development
- **Elementor Pro** — visual editing, landing page creation
- **МойСклад (MoySklad)** — ERP system, configuration, integrations, webhooks

### Tools and Environment
- **Git / GitHub** — version control, collaboration, pull requests
- **Linux / Windows** — cross-platform development
- **Docker** — containerization basics
- **jXLS** — report and template generation

### Methodologies and Approaches
- **REST API Design** — API architecture, best practices
- **Agile / Scrum** — sprint-based development, planning
- **Code Review** — peer code review and feedback
- **Version Control** — branch management, merge strategies

---

## 💻 Code Examples

### Example 1: Codewars Solution

**Task:** [Sum of Digits Digital Root](https://www.codewars.com/kata/50654ddff44f800200000004/train/javascript)

```javascript
// Solution: Calculate the digital root of a number
function digitalRoot(n) {
  // Basic approach using iteration
  while (n >= 10) {
    n = n
      .toString()
      .split('')
      .reduce((sum, digit) => sum + parseInt(digit), 0);
  }
  return n;
}

// Optimized approach using mathematical formula
function digitalRootOptimized(n) {
  return n === 0 ? 0 : (n - 1) % 9 + 1;
}

// Usage examples:
console.log(digitalRoot(16)); // 7 (1 + 6 = 7)
console.log(digitalRoot(493193)); // 2 (4 + 9 + 3 + 1 + 9 + 3 = 29 → 2 + 9 = 11 → 1 + 1 = 2)
console.log(digitalRootOptimized(16)); // 7
```

### Example 2: Telegram Bot Integration (Node.js/Telegraf)

```javascript
// Example from Watson DJ project: Telegram integration with MoySklad ERP
const Telegraf = require('telegraf');
const axios = require('axios');

const bot = new Telegraf(process.env.BOT_TOKEN);

// Handle /start command with deep linking for user registration
bot.start(async (ctx) => {
  const deepLinkToken = ctx.startPayload;

  if (deepLinkToken) {
    try {
      // Generate token in database and link with Telegram user
      const response = await axios.post('https://api.moysklad.ru/webhooks', {
        token: deepLinkToken,
        telegramUserId: ctx.from.id,
        timestamp: new Date().toISOString(),
      });

      ctx.reply(
        '✅ Registration successful! You will now receive shipping notifications.'
      );
    } catch (error) {
      ctx.reply('❌ Registration error. Please try again later.');
    }
  }
});

// Handle text messages for order status requests
bot.on('text', async (ctx) => {
  const orderNumber = ctx.message.text;

  try {
    const response = await axios.get(
      `https://api.moysklad.ru/api/remap/1.2/entity/customerorder/${orderNumber}`
    );

    ctx.reply(`📦 Order status: ${response.data.state.name}`);
  } catch (error) {
    ctx.reply('❌ Order not found.');
  }
});

bot.launch();
```

### Example 3: Vue.js Component (WooCommerce Store Optimization)

```vue
<template>
  <div class="product-variant-selector">
    <div class="color-swatches">
      <button
        v-for="variant in variants"
        :key="variant.id"
        :style="{ backgroundColor: variant.color }"
        :class="{ active: selectedVariant.id === variant.id }"
        @click="selectVariant(variant)"
        class="swatch"
        :title="variant.name"
      ></button>
    </div>

    <div class="variant-gallery" v-if="selectedVariant">
      <div class="main-image">
        <img :src="selectedVariant.mainImage" :alt="selectedVariant.name" />
      </div>
      <div class="thumbnails">
        <img
          v-for="(img, index) in selectedVariant.gallery"
          :key="index"
          :src="img"
          :alt="`${selectedVariant.name} - ${index + 1}`"
          @click="selectedImage = img"
          class="thumbnail"
        />
      </div>
    </div>

    <div class="variant-info">
      <h3>{{ selectedVariant.name }}</h3>
      <p class="price">{{ selectedVariant.price }} UZS</p>
      <button @click="addToCart" class="btn-add-to-cart">
        Add to Cart
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductVariantSelector',
  data() {
    return {
      variants: [
        {
          id: 1,
          name: 'Red',
          color: '#FF0000',
          price: 50000,
          mainImage: '/images/product-red-main.jpg',
          gallery: [
            '/images/product-red-1.jpg',
            '/images/product-red-2.jpg',
            '/images/product-red-3.jpg',
          ],
        },
        {
          id: 2,
          name: 'Blue',
          color: '#0000FF',
          price: 50000,
          mainImage: '/images/product-blue-main.jpg',
          gallery: [
            '/images/product-blue-1.jpg',
            '/images/product-blue-2.jpg',
          ],
        },
      ],
      selectedVariant: null,
      selectedImage: null,
    };
  },
  mounted() {
    this.selectedVariant = this.variants[0];
    this.selectedImage = this.variants[0].mainImage;
  },
  methods: {
    selectVariant(variant) {
      this.selectedVariant = variant;
      this.selectedImage = variant.mainImage;
    },
    addToCart() {
      this.$emit('add-to-cart', this.selectedVariant);
      alert(`${this.selectedVariant.name} added to cart!`);
    },
  },
};
</script>

<style scoped>
.product-variant-selector {
  max-width: 600px;
  margin: 20px auto;
}

.color-swatches {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.swatch {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: 2px solid #ccc;
  cursor: pointer;
  transition: all 0.3s ease;
}

.swatch.active {
  border-color: #000;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
}

.variant-gallery {
  margin-bottom: 20px;
}

.main-image img {
  width: 100%;
  border-radius: 8px;
  margin-bottom: 10px;
}

.thumbnails {
  display: flex;
  gap: 10px;
}

.thumbnail {
  width: 80px;
  height: 80px;
  object-fit: cover;
  border-radius: 4px;
  cursor: pointer;
  border: 2px solid transparent;
  transition: border-color 0.3s ease;
}

.thumbnail:hover {
  border-color: #999;
}

.variant-info {
  background: #f5f5f5;
  padding: 15px;
  border-radius: 8px;
}

.price {
  font-size: 24px;
  font-weight: bold;
  color: #27ae60;
  margin: 10px 0;
}

.btn-add-to-cart {
  width: 100%;
  padding: 12px;
  background: #27ae60;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 16px;
  transition: background 0.3s ease;
}

.btn-add-to-cart:hover {
  background: #229954;
}
</style>
```

---

## 💼 Work Experience

### Software Integration Specialist | Watson DJ
**Period:** March 2026 – July 2026
**Location:** Tashkent, [watsondj.uz](https://watsondj.uz)
**Industry:** Heating equipment retail / Business automation

**Project:** Warehouse Automation — Telegram + МойСклад (MoySklad) Integration
**Technologies:** Node.js, TypeScript, Telegraf, MoySklad API, REST API, PostgreSQL

**Key Achievements:**
- ✅ Designed and implemented an automated counterparty onboarding system via Telegram bots
- ✅ Reduced client registration time from ~5 minutes to ~3 minutes (40% optimization)
- ✅ Configured 15+ webhooks in MoySklad for automated document processing
- ✅ Created data migration scripts for transferring 500+ records with data integrity
- ✅ Trained 8 staff members on the new system

**GitHub Repository:** [github.com/iibratik](https://github.com/iibratik)

---

### Technical Support Specialist (L3) | Terranova Software
**Period:** May 2024 – February 2025
**Location:** Tashkent, [terranovasoftware.eu](https://terranovasoftware.eu)
**Industry:** Software vendor — data accounting systems for utility meters

**Project:** Italian Vocabulary Learning App (Duolingo-style)
**Technologies:** Python, SQL Server, Windows Services, REST API

**Key Achievements:**
- ✅ Developed an interactive Italian language learning application with quizzes
- ✅ Provided L3 technical support to 5+ corporate clients
- ✅ Implemented automated testing processes
- ✅ Reduced response time for technical requests from 2 hours to 30 minutes

---

### PR-Webmaster | Instax Uzbekistan
**Period:** May 2026 – July 2026
**Location:** Tashkent, [instax.com.uz](https://instax.com.uz)
**Industry:** E-commerce / Photography products

**Project:** WooCommerce Store Development & Optimization
**Technologies:** WordPress, WooCommerce, Elementor Pro, PHP, CSS3

**Key Achievements:**
- ✅ Created a fully functional e-commerce store with 200+ products
- ✅ Implemented product filtering and sorting system
- ✅ Diagnosed and fixed critical GTranslate/Multisite error (500 errors) in 2 hours
- ✅ Improved website loading speed by 35%

**Website:** [instax.com.uz](https://instax.com.uz)

---

### Personal Projects

#### 🚗 3D Car Tuning Visualizer
**Description:** Interactive web application for 3D car model visualization and customization. Users can modify components, colors, and parts while seeing real-time results.
**Technologies:** Three.js, JavaScript, WebGL, Responsive Design
**Key Features:**
- Load and visualize 3D car models
- Change textures and materials of car parts
- Interactive camera controls (zoom, rotate, pan)
- Export results (screenshots, configuration)
- Mobile-responsive design

**GitHub:** [github.com/iibratik/3d_tunung](https://github.com/iibratik/3d_tunung)
**Status:** Active Development

#### 📚 Course Reminder Bot
**Period:** August 2026
**Description:** Telegram bot for sending study reminders with LLM-based quiz generation and scheduling
**Technologies:** Python, aiogram, Ollama (Local LLM), APScheduler, SQLite
**Key Features:**
- Course reminder scheduling
- Automatic quiz generation via local LLM
- Learning progress tracking
- User schedule integration

**Status:** Active Development

#### 🤖 Partner Onboarding Bot (Watson DJ)
**Description:** Automated system for counterparty onboarding using deep links and tokens
**Technologies:** Node.js/TypeScript, Telegraf, MoySklad API, PostgreSQL
**Key Features:**
- Personal deep-link token generation
- Automatic Telegram user registration
- Data synchronization with MoySklad ERP
- Shipping document delivery via Telegram

**Status:** Production (Used in Watson DJ)

#### 🎨 ComfyUI Image Generation Pipeline
**Description:** Local image generation pipeline using Stable Diffusion on RTX 4070 GPU
**Technologies:** Python, ComfyUI, Stable Diffusion, CUDA, WebUI
**Key Features:**
- Local image generation (no cloud dependency)
- Custom workflow nodes
- RTX 4070 optimization (8GB VRAM)
- Integration with other applications via API

**Status:** Production (Personal use)

---

## 🎓 Education

### IT Park University
**Period:** 2022 – 2023
**Specialization:** Software Engineering
**Achievements:** Completed coursework with practical development experience

### Courses and Training

| Course | Platform | Year | Topic |
|--------|----------|------|-------|
| Claude Platform 101 | Anthropic | 2026 | AI/LLM integration in applications |
| HTML Course | Stepik | 2023 | Web development basics |
| Web Programming | ProWeb | 2022 | Full-Stack fundamentals |
| Git & GitHub | Self-Study | 2023 | Version control and collaboration |
| REST API Design | Self-Study | 2024 | API architecture and design |
| Docker Basics | Self-Study | 2025 | Containerization |

---

## 🌐 English Language

### Proficiency Level: **Professional (B2)**

### Language Practice:

- **Reading** 📖
  - Framework documentation (Vue.js, React, Next.js)
  - Technical articles on Medium, Dev.to, Habr
  - GitHub issues and pull requests
  - API documentation
  - ~2-3 hours per day

- **Writing** ✍️
  - Code comments in English
  - Git commit messages
  - Project documentation
  - Messages in international Slack channels
  - Answers in technical forums

- **Listening** 👂
  - Video tutorials (Traversy Media, The Net Ninja)
  - Tech podcasts (JavaScript Jabber, Syntax FM)
  - Webinars on Udemy and Coursera
  - ~1-2 hours per week

- **Speaking** 🗣️
  - Participate in technical discussions with English-speaking developers
  - Presented Watson DJ project in English
  - Regular communication in Discord developer communities

### Certificates:
- <!-- Add if available (IELTS, TOEFL, Cambridge, Duolingo) -->

---

## 📌 Additional Information

### Interests and Hobbies:
- 🤖 Local LLMs and AI integration (Ollama, ComfyUI)
- 🎨 Image generation and computer vision
- 🔧 DevOps and process automation
- 📚 Continuous learning of new technologies

### Availability:
- ✅ Open to relocation to European countries
- ✅ Available for remote work
- ✅ Open to business travel
- ✅ Flexible employment terms (full-time, contract-based)

### Career Preferences:
- **Remote Work:** Preferred, with occasional in-office meetings
- **Work Schedule:** Full-time, 5 days per week
- **Time Zone:** UTC+5, flexible with meetings in other time zones
- **Relocation:** Ready for European countries (visa sponsorship welcome)

---

**CV last updated:** September 2026
**GitHub Profile:** [github.com/iibratik](https://github.com/iibratik)
**LinkedIn:** [linkedin.com/in/iibratik](https://linkedin.com/in/iibratik)
