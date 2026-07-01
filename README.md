# AutoQTE-SolsRNG

An automated Python tool to instantly solve WASD QTE and escape boss stuns in Sol's RNG (Roblox).

## Description
- **Vietnamese:** Cong cu tu dong nhan dien chu cai (W, A, S, D) tren man hinh va tu dong gia lap bam phim de nhanh chong thoat khoi hieu ung khong che (Stun) cua Boss trong che do Hell Mode cua tua game Sol's RNG tren Roblox.
- **English:** An automated Python tool to instantly detect WASD characters on screen and automatically simulate key presses to quickly escape Boss stuns in Sol's RNG Hell Mode (Roblox).

## Dependencies
This tool requires the following Python libraries for screen capturing, image processing, and hardware-level key simulation:
- opencv-python
- numpy
- mss
- keyboard
- pyautogui
- pydirectinput

## Installation and Usage Guide

Follow these steps to set up the virtual environment and run the script on your local machine:

1. Create a virtual environment:
   `python -m venv .venv`

2. Activate the virtual environment (Windows):
   `.\.venv\Scripts\activate`

3. Install required libraries:
   `pip install -r requirements.txt`

4. Run the script:
   `python main.py`

5. Calibrate the screen coordinates:
   Click the "Calibrate ROIs" button on the tool's interface. Hover your mouse over the center of each QTE slot in the game, then press the numbers 1, 2, 3, 4, and 5 on your keyboard as prompted in the terminal to save the positions.

## Setting up requirements.txt

If you haven't created the requirements file yet, create a file named `requirements.txt` in the root directory and paste the following content into it:

opencv-python
numpy
mss
keyboard
pyautogui
pydirectinput
