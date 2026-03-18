# Parallel Programming Image Processor

## 📌 Project Overview
This project is a high-performance image processing system designed to evaluate and compare the efficiency of sequential execution versus multithreaded processing. Built as part of the Software Engineering program at the University of Europe for Applied Sciences, the application allows real-time visualization of performance metrics.

## 🚀 Tech Stack & Tools Used
* **Language:** C++
* **Parallelism & Concurrency:** POSIX threads (Pthreads), OpenMP
* **Graphical Interface:** OpenGL, ImGui

## ⚙️ Core Operations & Features
The application performs computationally intensive operations on 1280x1280 resolution images, applying the following transformations:
1. **Gaussian Blur:** Uses a 2D convolution kernel based on a continuous Gaussian function to apply blur. This operation was parallelized by distributing image rows across different threads.
2. **Rotation:** Reorients the image (90°, 180°, or 270° clockwise) by computing original coordinates and transforming them into a new image buffer.
3. **Brightness & Contrast Adjustment:** Modifies pixel intensity using a linear transformation formula applied independently across all pixels.
4. **Race Condition Simulator ("Apply All Filter"):** A compound function that executes all three filters simultaneously. This was intentionally designed to simulate a classic race condition on a shared image buffer, requiring thread synchronization via mutexes and critical sections.

## 📊 Key Performance Results
* **Multithreading Efficiency:** Parallelism reduced processing time for the Gaussian blur operation by more than 80% (from ~3900ms sequentially to ~687ms using OpenMP).
* **Thread Scaling:** Execution time consistently decreased as the number of threads increased from 1 to 4, with performance flattening out around 5 to 6 threads.
* **Synchronization Overhead:** The "Apply All Filter" experiment demonstrated that while parallel processing is powerful, enforcing mutual exclusion on shared memory introduces overhead that can force operations to execute sequentially.

## 💡 What I Learned
Developing this system provided deep, practical experience in low-level parallel programming. I successfully implemented manual thread management with Pthreads and compiler-directed parallelism with OpenMP. Furthermore, resolving the "Apply All Filter" race condition solidified my understanding of how to manage shared data safely using mutual exclusion.
