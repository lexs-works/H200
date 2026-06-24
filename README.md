![H200 · IN DEVELOPMENT](https://img.shields.io/badge/H200-WIP-c8a86b?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyMCIgaGVpZ2h0PSIyMCIgdmlld0JveD0iMCAwIDI0IDI0IiBmaWxsPSJub25lIiBzdHJva2U9IiNjOGE4NmIiIHN0cm9rZS13aWR0aD0iMiIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIiBzdHJva2UtbGluZWpvaW49InJvdW5kIj48Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSIxMCIvPjxwYXRoIGQ9Ik0xMiA4djRsMiAyIi8+PC9zdmc+)

[[EN](https://github.com/lexs-works/H200/blob/master/README.md) • [DE](https://github.com/lexs-works/H200/blob/master/README.de.md) • [RU](https://github.com/lexs-works/H200/blob/master/README.ru.md)]

# 🚀 H200 — A Soldering Station in a Marker-Sized Body, Powered by USB-C

> **H200 / Solderis OS Version:** 0.α.0626 (AEGIS VerSystem) <br/>
> **Primary Repository:** [~ax-hack/H200](https://git.sr.ht/~ax-hack/H200)

**H200 (Hacked 200)** is a deep hacker remaster of the popular PTS200 V2 soldering iron. Its original ergonomics are retained and enhanced with a proprietary non-slip coating. The budget internals have been entirely discarded and replaced with an industrial-grade, fault-tolerant component base.

This is a soldering station in a body the size of a marker pen — as reliable as Solaris, as simple as UNIX v6. Designed for professional servicing of complex electronics and precision R&D assembly.

Why a soldering station, rather than a soldering iron? Many are accustomed to the idea that a soldering station is a box with a cord, on which one sets a temperature. But time moves on, technology advances — today we can fit regulation and temperature hold within a pencil-shaped body, and do it properly, with deviation no greater than ±1 °C.

This is achieved through a robust industrial controller, the use of analogue circuit elements, and an uncompromising operating system written specifically for this station — Solderis OS.

This is a premium-segment instrument, free of planned obsolescence. Its warranted service life is 10 years, guaranteed first and foremost by the component base, the circuit design, and the build quality.

In the soldering station, hardware protection is backed up by an analogue equivalent, of near-instantaneous action:

- against short circuits
- against system shock — even if the tip is plunged into a block of ice, the station will continue heating it
- against power supply ripple

## 🔥 Dual-Polarity Tip Support

This is the project's point of origin. I was misled by Google AI when selecting a soldering iron for precision work under a microscope. Its hallucination informed me that the PTS200 V2 could accept C210 tips via an external adapter and custom firmware.

Having spent not very long being annoyed, I studied the subject and thought — if it doesn't exist, why not make it? Thus was born the concept of a soldering iron, in an ergonomic body, with support for two fundamentally different tip families.

### 🪓 Tip Physics: Supported Cartridges

#### Family 1: Two-Wire Cartridges (TS100 / TS101 / T12)

Physics: Heater and thermocouple are connected in series within a sealed cartridge. The tip has two contacts (positive and negative). The signal is of positive polarity (+9 mV at 350 °C).

#### Family 2: Three-Wire Cartridges (C210 / JBC-style)

Physics: Heater and thermocouple are decoupled and connected in parallel. The tip has three contacts: heater positive, common ground, and a dedicated thermocouple signal contact. The signal is continuous, but of negative polarity relative to ground (-13 mV at 350 °C). Feeding it directly to an MCU input will destroy the silicon.

> **Engineering Result:** You can use ultra-short C210 tips via an adapter cable with a lightweight remote handpiece for jeweller-grade WLCSP soldering under a microscope, and then — having switched profiles in the menu — change the H200 Pro over to a heavy, heat-capacitive T12 tip for warming massive ground polygons on multilayer boards.

## 💪 Problems the Station Solves

### Assembly on Multilayer Boards with High Thermal Dissipation

An honest 100 W of power into low-resistance cartridges, with full hardware support for heavy T12-series tips via a swappable adapter. The physical mass of the metal provides thermal stability across unbroken ground planes.

### Microsurgery and Trace Repair Under BGA Components

Connection of a JBC C210 remote handpiece via a flexible interface cable. Switching Solderis OS into differential inverting acquisition mode allows precise control of the negative voltage from the JBC thermocouple.

And the finely tuned assembly PID code delivers thermocouple control latency measured in nanoseconds.

### Uninterrupted 24/7 Commercial Operation

An analogue comparator cuts off a current short 15 nanoseconds ahead of the CPU's response. The input is clamped by a TVS suppressor against mains-borne ripple, and the transflective LCD is hardware-protected against burn-in and electrostatic discharge (ESD).

## 💣 Key Technological Decisions

1. **Analogue Armour — Hardware Short-Circuit Cutoff**
2. **Immunity to Power Supply Ripple**
3. **Omnivorous: Two Polar Families of Tips:**
    * *TS100/TS101/T12*
    * *C210 (JBC-style)*
4. **Transflective LCD in Place of OLED**
5. **Hybrid Sleep Without Core Polling**

## ⚙️ Operating System

For the H200 soldering station, a bespoke event-based operating system has been designed and is under development: Solderis OS.

System Philosophy: Solaris-grade reliability, with UNIX v6 simplicity.

The operating system is written in ARM Thumb-2 Assembler and C89. No compromises — only reliability, simplicity, and performance.

The operating system is built around a non-blocking ring buffer.

## 💯 200% Open Source

The entire project will be opened, from the manufacturing process for the body to the source code of the assembler internals.

The source code will be hosted in the official repository, on SourceHut: [~ax-hack/h200](https://git.sr.ht/~ax-hack/H200). The full code for all components will be published upon the conclusion of the crowdfunding campaign.

### Tools Used in H200 Development

In the development of the soldering station, I use my preferred open-source tools:

- BRL-CAD
- NGSPICE
- KiCAD
- etc.

## 🔏 Protection Against Counterfeiting

Openness creates a 100% risk of counterfeits. As the saying goes — take it and build it. The original device, from the developer, with a 10-year warranty, will be signed with an unforgeable cryptographic key based on PUF cryptography.

All official devices will be registered in the developer's site database. For identification, the device is connected to a computer via USB, and identification is performed on a dedicated area of the site — original devices will gain the ability to receive lightweight updates and access the author's library of calibration data for tips.

The author understands the inevitability of cloning, even with closed source code. The author also loves and respects Open Source culture — hence the decision to open the platform completely.

The price of an original device, when purchased through crowdfunding, represents not only the cost of the author's brainware, but also the cost of an honest 10-year warranty and service.

## 🚚 How to Acquire the H200 Portable Soldering Station?

At this moment — no way. The author is working on the research prototype and the operating system implementation. But you can accelerate the approach of the next stage by the following means:

- A donation for coffee and rosin via the GitHub button
- A star on GitHub.

### Stages of Market Entry and Product Versions:

* **H200 Pro** Founders Edition — a run of 97 units. The standard version of the soldering station, based on a printed circuit board, but component placement is carried out personally by the author under a microscope.
* **H200 Medusa** Creator's Edition — a run of 3 units. 3 collector's editions; engineering art — soldered in free-wire construction, with a sapphire viewing window in the body — for observing the internal beauty.
* **H200 Pro** — a small-batch production run, to be released according to demand, fully factory-soldered.

The product launch is planned via crowdfunding.

### ✅️ Crowdfunding and Founders Edition

The pre-order campaign will be launched for a strictly limited run — **100 units**, fully soldered, flashed, and tested personally by the author under a microscope. No third-party assembly houses. Only full quality control and an honest **10-year warranty**.

🥇 **The Ultimate Tier (only 3 units):**
The three backers who contribute the highest donation will receive an exclusive version, **H200 Medusa (Creator's Edition)**: a soldering iron with a sapphire-glass viewing window. Inside, the processor and its surrounding circuitry are visible, assembled by hand by the author using the "Medusa" free-wire method, with fine, lacquered microwires. For these three devices, a unique cryptographic certificate will be generated.

### 🔄 Versioning (AEGIS)

The project follows the **AEGIS** versioning system (see [AEGIS Specification](https://github.com/lexs-works/AEGIS)).
* Current milestone: **`0.α.0626`**
* Status: The theoretical architecture of the hardware-software platform has been completed. Manual assembly of the research R&D bench **"Medusa Proto"** is underway, using free-wire construction on a copper baseplate, for validation of the analogue protection and debugging of the assembly PID code.

## 🌌 Future Milestone (GEN2): H200 Rad-Hard Edition

> **Current Status:** R&D concept design. A transition from silicon microelectronics to vacuum nanoelectronics and microelectromechanical systems (MEMS).

The next fundamental iteration of the H200 project will be designed for operation under conditions that will reliably kill any human being, but not this tool: open space, zones of hard solar radiation exposure, and the internal containment of destroyed nuclear reactors.

### Technological Manifesto of the Rad-Hard Version:

1. **Spindt Cathodes Instead of Silicon (Micro-Vacuum Triodes):**
   All silicon semiconductors (including MOSFETs and logic gates), vulnerable to radiation degradation and thermal runaway, will be entirely replaced by arrays of Spindt field-emission cathodes. Logic and power switching will be performed by microscopic vacuum triodes integrated directly into the substrate. Electrons travel through vacuum; therefore, gamma radiation and neutron flux are physically incapable of causing irreversible structural breakdown.
2. **MEMS Switching and Analogue Logic:**
   For the physical switching of measurement paths and power management, microelectromechanical systems (MEMS) will be employed. Mechanical micro-relays on silicon/metallic suspensions provide a physical break in circuits, absolute immunity to electromagnetic pulse (EMP), and radiation-induced noise.
3. **Survival Philosophy:**
   This soldering iron is designed to continue holding a steady 350 °C at the tip of a C210 needle even when the surrounding environment is incandescent with background radiation. It will remain standing as a monument to human engineering, when the engineer himself has turned to dust.

---

## ⚖️ Legal Disclaimer

> ⚠️ **IMPORTANT NOTICE:** All mentions of nuclear reactors, outer space, Spindt cathodes, radiation hardness, and systems of survival under apocalyptic conditions are exclusively the artistic fiction of the author, conceptual science-fantastical nonsense (cyberpunk fanfiction), and a marketing instrument for attracting attention to open-source culture. <br/> The author is an ordinary bullshitter-enthusiast who simply wants to solder 100 good soldering irons for iPhone repair. The device is not intended for operation in outer space or for use inside the Chernobyl Nuclear Power Plant. Honestly.

> Solaris is a registered trademark of Oracle Corporation. UNIX is a registered trademark of The Open Group. Trademarks are referenced solely in the context of qualitative product comparison.

## 📬 Contacts

If you have commercial proposals, B2B collaboration enquiries, or wish to discuss the architecture of Solderis OS outside of mailing lists:

* **⚡ Threema:** [9FM22ZUC](https://threema.id/9FM22ZUC) (Primary channel for rapid contact; ***please begin your message with [H200]***)
* **🌐 SourceHut Profile:** [~ax-hack](https://git.sr.ht/~ax-hack/)
* **🌐 SourceHut PROJECT REPO:** [~ax-hack/h200](https://git.sr.ht/~ax-hack/H200)
* **📧 Email:** `h200@lexs.work` (For formal enquiries and git-mail patches)

### 🔬 Engineering Community

I also run a closed Signal circle — a group where I publish working notes on engineering, architecture design, software development, and the hidden side of the commercial world.

Joining the group is by request via Threema, or via the Telegram bot: [@lexs_gatekeeper_bot](https://t.me/lexs_gatekeeper_bot).

<a name="crypto-donate"></a>
## ☕ Coffee & Colophony

If you like the idea behind this project and feel like throwing in for coffee and rosin, you can do so directly via crypto — no middlemen, no fuss.

| Coin / Network | Wallet Address | Check Balance |
| :--- | :--- | :--- |
| **Bitcoin (BTC)** | `bc1q3flezaz48a6a445yf5ncxyfkmkdr9u830kzqgv` | [🔍 Explorer](https://blockchair.com) |
| **Litecoin (LTC)** | `ltc1qqa0zd6p5aevp4wv0fxdvzujn9yykl6f8zudpj9` | [🔍 Explorer](https://blockchair.com) |
| **USDT** (Polygon / Arbitrum) | `0x1A645b36D41C38732cdB696dB8AAf2bCB38CB2E8` | [🔍 Explorer](https://blockchair.com) |

> ⚠️ A note on USDT: please send only via Polygon or Arbitrum — that way you won't get stung by Ethereum mainnet fees. The address is the same for both networks.