# WhatsApp-bot-viewer

1000 Bot WhatsApp Channel Viewer

A browser-based dashboard for simulating up to 1,000 virtual bots viewing a WhatsApp Channel URL.

The application provides:

- Virtual bot simulation
- Up to 1,000 simulated bots
- Configurable channel preview cards
- Start / Stop controls
- Automatic cycle restart
- Cycle counter
- Active/completed/error statistics
- Simulation progress bar
- Individual bot activity status
- WhatsApp Channel URL validation
- Responsive Bootstrap interface
- Dark-themed dashboard

«Important: The bots in this application are virtual UI simulations. They do not create 1,000 network requests to WhatsApp and do not artificially generate channel views, followers, reactions, or other engagement.»

---

Demo URL

The application is preconfigured with:

https://whatsapp.com/channel/0029Vb8wre3KbYMUWU4Efx1x

You can replace it with another WhatsApp Channel URL.

---

Features

Virtual Bots

The dashboard can display and simulate up to:

1,000 bots

Each bot has an individual status:

- Waiting
- Viewing channel...
- Completed
- Simulated error

The simulation processes bots in batches so that the browser does not attempt to create 1,000 simultaneous operations.

---

Simulation Statistics

The dashboard displays:

Statistic| Description
Bots| Total number of virtual bots
Active| Bots currently being simulated
Completed| Successfully completed simulations
Errors| Simulated errors
Progress| Percentage of completed simulations

The error rate is simulated locally and does not represent an actual WhatsApp error rate.

---

WhatsApp Channel Previews

WhatsApp Channel pages generally cannot be reliably embedded inside an HTML "<iframe>" because of browser security and embedding restrictions.

Instead, the application creates clickable preview cards.

Each card contains:

- WhatsApp branding
- Channel number
- Channel URL
- Open WhatsApp Channel button

Clicking the button opens the supplied channel URL in a new browser tab.

---

Auto Restart

The Auto Restart option is enabled by default.

When every virtual bot in the current cycle has finished:

1. The current cycle ends.
2. The dashboard displays "Restarting...".
3. A short delay occurs.
4. A new virtual simulation cycle begins.

Disable Auto Restart if you want the simulation to stop after one cycle.

---

Configuration

Virtual Bot Count

The number of simulated bots can be configured from:

1 - 1000

The default is:

1000

---

Channel Previews

The number of clickable preview cards can be configured to:

4
8
12
20

The default is:

20

These are only browser UI cards. They do not represent 20 independent WhatsApp users.

---

Project Structure

A minimal installation requires only one file:

project/
└── index.html

The Bootstrap CSS dependency is loaded from jsDelivr.

No backend is required for the virtual simulation.

---

Installation

1. Download or create the HTML file

Save the application as:

index.html

2. Open it

Double-click:

index.html

or serve it using a local web server.

For example:

python -m http.server 8000

Then open:

http://localhost:8000

---

Using the Application

Step 1

Enter a WhatsApp Channel URL.

Example:

https://whatsapp.com/channel/0029Vb8wre3KbYMUWU4Efx1x

Step 2

Choose the number of virtual bots.

Example:

1000

Step 3

Choose the number of channel preview cards.

Example:

20

Step 4

Click:

Start

The virtual bots will begin processing.

Step 5

Monitor:

- Active bots
- Completed bots
- Errors
- Progress
- Current cycle

---

Stopping the Simulation

Click:

Stop

This stops the simulation timers and cancels a pending automatic restart.

---

Clearing the Dashboard

Click:

Clear

This removes:

- Bot cards
- Preview cards
- Statistics
- Cycle information
- Simulation state

---

How the Simulation Works

The application does not launch real bots.

Instead, JavaScript maintains an internal state:

{
  total: 1000,
  active: 0,
  done: 0,
  errors: 0,
  cycle: 1,
  running: true
}

Bots are started in small batches.

Each bot is then given a randomized simulated completion delay.

A small percentage of bots are randomly assigned a simulated error.

For example:

if (Math.random() < 0.03) {
    // Simulated error
} else {
    // Completed
}

This is only for demonstrating the dashboard.

---

Security Considerations

The application validates that the supplied URL uses a supported WhatsApp URL format.

It also opens external channel URLs using:

target="_blank"
rel="noopener noreferrer"

This helps prevent the newly opened page from accessing the original page through "window.opener".

Only use URLs and channels that you own or are authorized to test.

---

Limitations

No Real WhatsApp Automation

This project does not:

- Create WhatsApp accounts
- Log users into WhatsApp
- Control WhatsApp accounts
- Send messages
- Follow channels
- Generate followers
- Generate reactions
- Generate views
- Manipulate WhatsApp analytics
- Send 1,000 requests to WhatsApp

The bot count represents virtual browser UI objects only.

No Embedded WhatsApp Page

The channel itself is not embedded in an iframe because WhatsApp may prevent third-party framing.

The preview cards instead provide direct links to the channel.

---

Technologies

The application uses:

- HTML5
- CSS3
- JavaScript
- Bootstrap 5.3
- Browser DOM APIs

No framework or backend is required.

---

Browser Compatibility

The application is designed for modern browsers supporting:

- ES6 JavaScript
- "URL"
- "DocumentFragment"
- "replaceChildren()"
- CSS Grid
- Bootstrap 5

Recommended browsers include current versions of:

- Chrome
- Edge
- Firefox
- Safari

---

Customization

You can change the default channel by editing:

<input
  id="url"
  class="form-control"
  type="url"
  value="https://whatsapp.com/channel/0029Vb8wre3KbYMUWU4Efx1x">

You can change the default bot count by modifying:

value="1000"

You can change the default preview count by modifying:

<option selected>20</option>

---

License

Use and modify this project according to the license terms you choose for your own distribution.

When using it with external services, comply with the applicable service terms, laws, and authorization requirements.
