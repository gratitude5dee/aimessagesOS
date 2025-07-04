***

# aiMessagesOS

<div align="center">
  <img src="https://raw.githubusercontent.com/GRATITUD3/aimessages/main/public/og-image.svg" alt="aiMessagesOS Logo" width="150">
  <h1>aiMessagesOS</h1>
  <p><strong>A beautiful, open-source, voice-and-text AI chat interface powered by Groq and React.</strong></p>
  <p>Built with the latest web technologies to deliver a seamless, high-performance conversational AI experience.</p>
</div>

<p align="center">
  <a href="https://github.com/gratitude5dee/aiMessagesOS-main/blob/main/LICENSE"><img src="https://img.shields.io/github/license/gratitude5dee/aimessagesOS-main?style=for-the-badge&color=blue" alt="License"></a>
  <img src="https://img.shields.io/github/package-json/v/gratitude5dee/aimessagesOS-main?style=for-the-badge&color=blueviolet" alt="Version">
  <img src="https://img.shields.io/badge/built%20with-Vite-646CFF?style=for-the-badge&logo=vite" alt="Built with Vite">
  <img src="https://img.shields.io/badge/UI-shadcn/ui-black?style=for-the-badge&logo=shadcnui&logoColor=white" alt="shadcn/ui">
</p>

<!-- Optional: Add a hero image or GIF of the app in action -->
<!-- 
<p align="center">
  <img src="<URL_TO_YOUR_APP_SCREENSHOT_OR_GIF>" alt="aiMessagesOS Demo">
</p>
-->

## 🚀 Features

-   **⚡ Blazing Fast Responses:** Integrated with the [Groq LPU™ Inference Engine](https://groq.com/) for near-instant AI feedback.
-   **🗣️ Advanced Voice Conversations:** Real-time, voice-first interaction powered by [Vapi AI](https://vapi.ai) and on-device Voice Activity Detection (VAD).
-   **✨ Modern & Sleek UI:** A beautiful and responsive interface built with **React**, **Tailwind CSS**, and **shadcn/ui**.
-   **🎨 Stunning Visuals:** Smooth animations with **Framer Motion** and potential for 3D elements with **Three.js**.
-   **📊 Data Visualization:** Includes charting capabilities with **Recharts**.
-   **⚛️ Solid Foundation:** Built with **Vite** for a lightning-fast development experience and **React Query** for robust data management.
-   **📝 Type-Safe:** Fully configured for a great developer experience with path aliases and modern tooling.

## 🛠️ Tech Stack

A comprehensive list of the technologies that power aiMessagesOS:

-   **Framework:** [React 18](https://react.dev/)
-   **Build Tool:** [Vite](https://vitejs.dev/)
-   **Styling:** [Tailwind CSS](https://tailwindcss.com/)
-   **UI Components:** [shadcn/ui](https://ui.shadcn.com/)
-   **Language:** JavaScript (ESM)
-   **AI Inference:** [Groq SDK](https://console.groq.com/docs/sdk)
-   **Voice AI:** [Vapi AI](https://vapi.ai/)
-   **Voice Activity Detection:** [VAD Web](https://github.com/ricky0123/vad-web)
-   **Routing:** [React Router](https://reactrouter.com/)
-   **Data Fetching/State:** [TanStack Query (React Query)](https://tanstack.com/query/latest)
-   **Animations:** [Framer Motion](https://www.framer.com/motion/)
-   **Forms:** [React Hook Form](https://react-hook-form.com/) & [Zod](https://zod.dev/)
-   **Icons:** [Lucide React](https://lucide.dev/)
-   **Charting:** [Recharts](https://recharts.org/)
-   **3D Graphics:** [Three.js](https://threejs.org/)

## ✅ Prerequisites

Before you begin, ensure you have the following installed on your system:

-   [Node.js](https://nodejs.org/) (v18.0.0 or higher)
-   A package manager: [npm](https://www.npmjs.com/), [Yarn](https://yarnpkg.com/), or [Bun](https://bun.sh/)
-   API keys from the following services:
    -   [Groq](https://console.groq.com/keys)
    -   [Vapi](https://vapi.ai/) (if you plan to use voice features)

## 📦 Installation & Setup

Get your local development environment set up in just a few minutes.

### 1. Clone the Repository

```bash
git clone https://github.com/GRATITUD3/aiMessagesOS.git
cd aiMessagesOS
```

### 2. Set Up Environment Variables

This project requires API keys to connect to AI services. Create a `.env` file in the root of the project by copying the example below:

```bash
# Create the .env file
touch .env
```

Now, open the `.env` file and add your API keys.

**.env**
```env
# Get your Groq API key from https://console.groq.com/keys
VITE_GROQ_API_KEY="gsk_..."

# Get your Vapi API key from the Vapi dashboard
VITE_VAPI_API_KEY="..."

# Optional: Vapi Assistant ID if you have a specific one
VITE_VAPI_ASSISTANT_ID="..."
```
> **Important:** The `VITE_` prefix is required by Vite to expose these variables to the client-side code. Do not remove it.

### 3. Install Dependencies

You can use `npm`, `yarn`, or `bun`. Choose your preferred package manager.

```bash
# Using npm
npm install

# Using yarn
yarn install

# Using bun
bun install
```

## ▶️ Usage

Once the dependencies are installed and your environment variables are set, you can run the development server.

```bash
# Using npm
npm run dev

# Using yarn
yarn dev

# Using bun
bun run dev
```

The application will be available at `http://localhost:8080` by default.

## 🧪 Testing

Currently, this project does not have a formal testing suite. This is a fantastic area for contribution! We recommend using [Vitest](https://vitest.dev/) for unit/integration tests and [Playwright](https://playwright.dev/) or [Cypress](https://www.cypress.io/) for end-to-end tests.

If you'd like to contribute, please feel free to open a Pull Request to set up a testing framework.

## 🚀 Deployment

This is a standard Vite-based React application and can be deployed to any static hosting service.

### Recommended Platforms

Services like [Vercel](https://vercel.com/), [Netlify](https://www.netlify.com/), or [Cloudflare Pages](https://pages.cloudflare.com/) provide an excellent, zero-configuration deployment experience.

1.  Push your code to a Git repository (GitHub, GitLab, etc.).
2.  Connect your repository to your hosting provider.
3.  Configure the build command: `npm run build` (or `yarn build`, `bun run build`).
4.  Set the output directory to `dist`.
5.  **Important:** Remember to add your environment variables (`VITE_GROQ_API_KEY`, etc.) in the project settings on your hosting provider's platform.

### Docker

For self-hosting, you can use the provided `Dockerfile` to build a production-ready container image.

```Dockerfile
# Dockerfile

# Stage 1: Build the application
FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Serve the application with a lightweight server
FROM nginx:stable-alpine
COPY --from=builder /app/dist /usr/share/nginx/html
# Copy a custom nginx config if needed
# COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

## 🤝 Contributing

We welcome contributions of all kinds! Whether it's fixing bugs, adding new features, improving documentation, or setting up tests, your help is appreciated.

### How to Contribute

1.  **Fork the repository** on GitHub.
2.  **Create a new branch** for your feature or bug fix:
    ```bash
    git checkout -b feature/your-awesome-feature
    ```
3.  **Make your changes** and commit them with a clear, descriptive message.
4.  **Push your branch** to your forked repository.
5.  **Open a Pull Request** to the `main` branch of the original repository.

Please ensure your code adheres to the existing style and that you have run the linter.

## 🛣️ Roadmap

Here are some ideas for future development:

-   [ ] **Conversation History:** Save and load past conversations.
-   [ ] **User Authentication:** Allow users to sign in and save their settings.
-   [ ] **Model Selection:** Add a UI to switch between different AI models available via Groq.
-   [ ] **Enhanced 3D Visuals:** Integrate the Three.js elements more deeply into the UI.
-   [ ] **Theme Customization:** Allow users to change the color scheme and layout.
-   [ ] **Testing Suite:** Implement comprehensive unit, integration, and e2e tests.
-   [ ] **PWA Support:** Make the application installable as a Progressive Web App.

## 📜 License

This project is licensed under the **MIT License**. See the [LICENSE](./LICENSE) file for more details.

## 🙏 Acknowledgments

This project stands on the shoulders of giants. A huge thank you to:

-   The teams behind **React**, **Vite**, and **Tailwind CSS** for their incredible tools.
-   **shadcn** for creating the exceptional `shadcn/ui` component library.
-   The **Groq** and **Vapi** teams for making their powerful AI services accessible.
-   All the open-source contributors whose packages make this project possible.
