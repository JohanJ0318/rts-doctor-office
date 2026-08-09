# Real-Time Doctor's Office System

Project showcase page for an **ESP32 + FreeRTOS** embedded system that simulates patient
flow in a medical imaging facility under hard real-time deadlines.

**[View the live page →](https://johanj0318.github.io/rts-doctor-office/)**

UCF — Real-Time Systems, Fall 2025.

## The project

Four FreeRTOS tasks with priority-based preemptive scheduling manage patient check-in,
doctor availability, and X-ray positioning:

- **Check-in** — ISR-driven button with hardware debouncing; a binary semaphore admits
  exactly one patient per press so the queue can't be corrupted.
- **Queue** — up to 200 patients across two concurrent doctors, using counting semaphores
  to preserve FIFO order and prevent double-booking.
- **X-ray positioning** — an HC-SR04 ultrasonic sensor verifies the patient is in the
  100–375 cm safe zone. Highest task priority, because this is the life-safety path.
- **Timing** — all hard deadlines verified with a logic analyzer.

**Stack:** ESP32 DevKit C V4 · FreeRTOS · ESP-IDF (C) · Wokwi simulator · logic analyzer.
5 synchronization primitives (binary semaphore, mutex, counting semaphore, 2 queues),
1 ISR, 4 tasks.

## Links

- [Live simulation (Wokwi)](https://wokwi.com/projects/449489603477648385)
- [Video demo (90 s)](https://youtu.be/wCfJREWKhaA)

> This repository contains the showcase page itself (`index.html`), served via GitHub Pages.
