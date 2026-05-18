## SSH Terminal Portfolio – Practical Guide
📌 What is an SSH Portfolio?
An SSH Portfolio is an open-source, interactive Terminal User Interface (TUI) served entirely over a secure shell connection. It is designed to provide developers with a unique, lightweight way to showcase resumes, projects, and live experience directly inside a user's native terminal window.
Unlike traditional web-based portfolios, an SSH portfolio operates entirely in the text realm, eliminating browser rendering overhead and JavaScript tracking while delivering a highly technical first impression.
What an SSH Portfolio is used for
An SSH portfolio is deployed by developers and engineers to centralize their professional presence in a geek-friendly format.
It is used for:

* Presenting structured resumes without bulky PDF files
* Creating and managing interactive project directories with external links
* Demonstrating live coding capabilities and system engineering skills
* Embedding dynamic copy-to-clipboard contact portals (Email, GitHub, LinkedIn)
* Segmenting professional info using clean, keyboard-driven UI menus
* Acting as a lightweight sandbox for custom TUI widgets and experiments

Where an SSH Portfolio can run
An SSH portfolio is highly flexible and can be self-hosted on various environments depending on infrastructure preferences:

* Cloud virtual private servers (VPS) like DigitalOcean, AWS EC2, or Linode
* Edge hosting networks supporting persistent TCP connections (e.g., Fly.io)
* Local home lab machines or Raspberry Pis exposed through network tunnels

Why an SSH Portfolio is widely used
An SSH portfolio is popular because it combines retro terminal aesthetics with modern UX features that simplify data presentation. Instead of scrolling a heavy webpage, recruiters and engineers can navigate skills matrices, code snippets, and work histories via intuitive hotkeys.
It is often used as a full personal branding edge solution, replacing or supplementing traditional web templates while proving the author's capabilities in command-line environments.
Why Use an SSH Portfolio?
An SSH portfolio is widely adopted because it combines system-level engineering concepts with a clean interface, making advanced text-based routing and navigation accessible without heavy browser-side engines.
Advanced terminal UI navigation
An SSH portfolio provides a powerful stateful keyboard engine capable of handling responsive screen resizing, custom color palettes, grid layouts, and smooth animations inside text boundaries.
User-friendly terminal interface
Instead of relying on plain text output, an SSH portfolio offers structured visual sections. This makes it easier to browse markdown pages, project links, and experience timelines using intuitive hotkeys.
Excellent SSH access support
The system includes built-in support for multiple secure terminal authentication methods, allowing users to connect instantly without installing third-party apps:

* Native Unix/Linux/macOS Terminals
* Windows Command Prompt or PowerShell
* Mobile SSH clients (Termux, iNDS, etc.)

Real-time session monitoring
The platform provides developers with live visibility into active connections, connection metrics, and visitor footprints. This helps hosts quickly track portfolio engagement and optimize session timeouts.
Package system (extensibility)
The portfolio's internal engine can be extended with external libraries or APIs to enhance functionality, such as:

* Analytics tracking (session counts and geographic origins)
* Live project updates fetched directly via the GitHub API
* Easter-egg mini-games (e.g., terminal Snake or Tetris)

Overall, an SSH portfolio is used because it bridges the gap between low-level terminal protocols and practical usability, making it a strong choice for standing out to tech-focused engineering teams.
------------------------------
## Basic Concepts
Understanding an SSH portfolio starts with how it separates and controls application states through interactive layouts and server modules. The system is built around the idea that each terminal session must be securely handled and rendered.
Interfaces & Navigation
Menus inside an SSH portfolio represent different operational spaces. Each section can have its own navigation rules and layout options.

* Main Menu → Navigation hubThe primary screen loaded immediately upon client handshake completion.


* Handles initial visitor greeting and environment reading
* Typically the most scannable interface section
* Navigable using standard arrow keys or Vim hotkeys (j/k)


* View Modals → Content pagesThe sub-menus representing dedicated data views.


* Used by specific content lists (Resume, Skills, About Me)
* Usually responsive to standard escape (ESC) or back (b) commands
* Allows quick hopping between different operational nodes


* External Outlets → Link endpoints (GitHub, LinkedIn, Email)

Additional operational items used to connect terminal users to external assets.
They can be configured as:

* Terminal hyperlinks (OS-supported clickable text URLs)
* Text selection blocks for easy copy-pasting
* Automated terminal actions (triggering email prompts or clipboards)

These interfaces help compartmentalize personal information and keep layout presentations highly structured.
Session Handshaking
In an SSH portfolio, incoming terminal connections are managed on a designated network port, meaning each session gets its own independent runtime loop.
Connection loops define what UI components are drawn based on terminal type, dimensions, and theme settings.
👉 Common examples:

* Identify User → Welcome Banner
→ The server extracts the visitor's local terminal username to print a personalized welcome banner.
* Redraw Engine → Resize Action
→ Terminal windows trigger a redraw event, resizing internal box layouts to fit the new layout width safely.

TUI (Terminal User Interface)
Allows application builders to draw panels, lists, and text elements inside grids.
Stateful App Loop

* Tracks keyboard inputs and view updates
* Automatically re-renders screen changes instantly

SSH Protocol Server

* Secure remote shell processing
* Automated port management and key pairs

Data Engine (via JSON/YAML)

* Reads local data files
* Populates profile grids dynamically

Logging

* Connection logs
* Live active visitor sessions
* Performance overhead metrics

Installation (Quick Summary)

   1. Clone the project repository
   2. Generate local host keys for deployment
   3. Configure your text data arrays
   4. Start the application engine:

go run main.go --port 2222

Recommended Initial Setup

   1. Change the default port configurations
   * Default testing port: 2222
   2. Configure data files
   * Edit personal details in the asset data configurations (e.g., data.json)
   3. Deploy the application
   * Always keep dependencies and host keys secure
   
------------------------------
## Basic Security Rules
A secure application configuration is built on a simple but strict execution structure: limit shell capabilities by default, then explicitly allow only what is required for interface usage.
This approach eliminates system exploitation paths and ensures that your portfolio remains a secure viewing tool rather than an open backdoor.
🔸 Disable Interactive PTY Shell Shells (Default rule – very important)
By default, all system shell command execution paths (/bin/sh, /bin/bash) must be entirely blocked for connections.

* Prevents unsolicited system command access to the host
* Protects background host file directories from direct exposure
* Reduces application exploit vulnerabilities significantly

This configuration is the foundation of structural security in custom SSH tools.
🔸 Allow TUI Control → Quit Commands (So internal loops close normally)
Visitors reading content need a native path to drop connection sessions instantly via common key binds.

* Allows session closing via Ctrl+C, q, or ESC hotkeys
* Enables clear server-side connection cleaning routines
* Keeps system memory clear of dead/zombie terminal contexts

This exit logic ensures efficient connection processing and host performance.
🔸 Host Configuration (Open specific ports safely)
Port isolation rules ensure external traffic reaches the custom interface rather than administrative tools.
Instead of exposing root administration ports, specific routes are configured.
Example use case:

* Exposing your SSH portfolio securely to public network connections

This involves:

* Mapping custom system ports (2222) → public traffic routers (22)
* Restricting inbound traffic to the portfolio app container bounds
* Applying modern firewall rule groups to limit server access exposure

------------------------------
If you'd like to customize this further, tell me:

* The programming language or TUI framework you are using (e.g., Go/Bubble Tea, Node.js/Blessed, Python/Textual)
* The hosting platform you plan to use (e.g., Docker, a specific VPS, Fly.io)
* Any extra features you want to document (e.g., custom themes, visitor tracking, analytics)

I can tailor this guide exactly to your development stack!

