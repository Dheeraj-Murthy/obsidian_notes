## **Dheeraj Murthy, Lesin**

International Institute of Information Technology Bangalore (IIIT Bangalore)  
Collaboration with NIMHANS

## **Proposal / Abstract**

Transcranial Magnetic Stimulation (TMS) experiments require reliable Electromyography (EMG) signal acquisition to measure Motor Evoked Potentials (MEPs) and support neuroscience research. Current experimental workflows rely heavily on proprietary acquisition software, which limits flexibility, automation, and real-time control while also increasing dependency on closed research systems.   Preliminary EMG studies further showed that signal quality is highly sensitive to electrical interference, unstable power conditions, electrode placement, and hardware limitations, making reliable acquisition difficult in practical research environments.  

This project proposes the development of a lightweight real-time EMG acquisition system for TMS experiments using direct communication with Micro1401 hardware through CED drivers. The proposed software pipeline will support continuous EMG acquisition, live visualization, automated logging, and open-format data storage for integration with modern research and analysis tools.   In parallel, the project also proposes the development of a separate experimental EMG hardware pipeline focused on low-cost and modular EMG acquisition hardware for research applications. This includes exploration of custom amplification and filtering circuits, noise reduction mechanisms, portable acquisition modules, and standardized signal conditioning approaches to improve acquisition stability and signal quality. The combined software and hardware framework aims to create an affordable, extensible, and research-friendly EMG platform that can support future work in neuroscience, neuroengineering, rehabilitation systems, and biomedical signal analysis.

# **1. Introduction and Motivation**

Transcranial Magnetic Stimulation (TMS) is a non-invasive neurostimulation technique widely used in neuroscience and psychiatric research. During TMS experiments, magnetic pulses stimulate cortical neurons, producing measurable muscular responses known as Motor Evoked Potentials (MEPs). These responses are captured using Electromyography (EMG) systems and are critical for studying motor pathways, neuroplasticity, rehabilitation, and neurological disorders.

Most current TMS workflows rely heavily on proprietary EMG acquisition software and hardware ecosystems. While functional, these systems often introduce several limitations, including high cost, restricted automation capabilities, poor flexibility for data analysis, unstable software environments, and dependence on closed research infrastructure. These limitations slow down experimentation and reduce accessibility for smaller research labs.

At the same time, preliminary investigations using low-cost EMG systems showed that EMG acquisition is highly sensitive to environmental and hardware-related factors such as electrical interference, unstable power conditions, electrode placement, and patch degradation. These observations highlight the need for robust, flexible, and research-oriented EMG acquisition pipelines that are both affordable and customizable.

This project aims to address these challenges through the development of lightweight software and experimental hardware pipelines for real-time EMG acquisition in TMS research environments.

---

# **2. Problem Statement**

Current TMS EMG acquisition workflows rely on proprietary signal acquisition software that presents multiple practical limitations for neuroscience research.

Major challenges identified include:

- Heavy and unstable software environments
- Limited real-time control over acquisition workflows
- Restricted export and interoperability with modern analysis tools
- Poor automation support for scalable experiments
- Dependence on proprietary closed-source ecosystems
- Difficulty integrating with custom research pipelines

In addition to software limitations, low-cost EMG experimentation revealed several signal reliability challenges:

- Electrical interference (EMI) causing severe baseline distortion
- Signal instability under low power conditions
- Sensitivity to electrode placement
- Signal degradation due to patch reuse
- Need for standardized acquisition procedures

These issues collectively reduce the flexibility, reproducibility, and scalability of neuroscience experiments.

---

# **3. Project Objectives**

The primary objective of this work is to develop a lightweight, open, and extensible EMG acquisition framework for TMS experiments.

## **Software Objectives**

- Develop a real-time EMG acquisition system using direct communication with Micro1401 hardware
- Enable live signal visualization for experiment monitoring
- Support open-format storage and export of acquired signals
- Improve acquisition throughput and responsiveness
- Reduce dependence on proprietary signal acquisition software
- Build a flexible foundation for future automated analysis pipelines

## **Hardware Objectives**

- Explore development of low-cost modular EMG acquisition hardware
- Design signal conditioning and amplification pipelines
- Investigate methods for noise reduction and EMI mitigation
- Develop portable and research-friendly acquisition modules
- Improve acquisition stability and signal quality
- Create a scalable platform for future neuroengineering and biomedical signal processing research

---

# **4. Work Completed**

## **4.1 Initial EMG Investigation**

Initial work focused on understanding the practical challenges involved in EMG signal acquisition using a low-cost EMG sensor module integrated with an Arduino-based acquisition setup.

The setup included:

- EMG sensor module
- Arduino-based analog acquisition
- Surface electrodes
- Breadboard and ancillary circuitry
- Python-based visualization and logging tools

The acquired data was streamed through serial communication and visualized in real time for analysis.

This stage helped establish a foundational understanding of signal behavior, hardware limitations, and environmental noise sources affecting EMG acquisition.

---

## **4.2 Controlled Noise Experiments**

Several controlled experiments were conducted to identify and quantify major contributors to EMG signal degradation.

### **Power Supply Stability**

Testing revealed that the EMG acquisition system was highly voltage-sensitive. Low-voltage conditions resulted in complete signal loss, demonstrating the importance of stable power delivery for reliable acquisition.

### **Acoustic Noise**

Experiments involving external audio sources showed only minor effects on the EMG baseline, indicating that acoustic interference had limited impact on signal integrity.

### **Electrical Interference (EMI)**

Electrical interference was identified as the most severe noise source. The presence of nearby charging cables and electronic devices significantly raised baseline signal levels, often overlapping with genuine muscle activity.

### **Electrode Placement and Patch Reusability**

Signal quality was found to vary considerably depending on electrode positioning and patch condition. Reused electrode patches introduced additional noise and reduced signal consistency.

These observations demonstrated the importance of standardized acquisition procedures and motivated the exploration of improved hardware and filtering mechanisms.

---

## **4.3 Real-Time TMS EMG Acquisition Pipeline**

Following the initial EMG studies, the project expanded into developing a dedicated EMG acquisition pipeline for TMS experiments.

The primary goal was to replace proprietary acquisition software with a lightweight and flexible alternative.

The developed architecture consisted of:

- Direct communication with Micro1401 hardware using CED drivers
- Continuous EMG signal acquisition
- Real-time visualization pipeline
- Open-format data storage
- Automated logging mechanisms

An initial Python-based prototype was developed to validate feasibility.

The prototype successfully implemented:

- Device communication
- EMG signal reading
- Real-time plotting
- Signal storage in open formats

This validated the practicality of building a custom acquisition system outside proprietary ecosystems.

---

## **4.4 Performance Optimization and C++ Migration**

Although the Python implementation enabled rapid prototyping, performance limitations became apparent during real-time acquisition.

Observed throughput was approximately:

- Python implementation: ~1 kSamples/s

This was insufficient for smooth high-frequency monitoring required during TMS experiments.

To improve performance, the acquisition layer was reimplemented in C++.

The optimized implementation achieved:

- Approximately ~20 kSamples/s throughput
- Significantly improved responsiveness
- Reduced acquisition bottlenecks
- Improved real-time visualization performance

The migration demonstrated the feasibility of a lightweight high-performance acquisition pipeline suitable for practical neuroscience workflows.

---

# **5. System Architecture**

The current acquisition architecture consists of the following pipeline:

Micro1401 Device  
↓  
CED1401 Drivers/API  
↓  
Custom Acquisition Layer  
↓  
Real-Time Visualization  
↓  
CSV/Open Data Storage  
↓  
Analysis Pipelines

The modular design allows future integration with additional hardware modules, filtering systems, automated analysis tools, and machine learning workflows.

---

# **6. Experimental Findings and Observations**

The project produced several important experimental observations relevant to EMG acquisition reliability.

## **Major Findings**

### **Electrical Interference as Primary Noise Source**

EMI was identified as the most disruptive factor affecting EMG acquisition. Nearby electronic devices and charging cables introduced severe baseline shifts that could overlap with valid muscle signals.

### **Voltage Stability is Critical**

Stable power supply conditions were essential for reliable acquisition. Low voltage conditions caused complete signal failure.

### **Electrode Quality and Placement Significantly Affect Signal Integrity**

Patch degradation and inconsistent electrode placement produced increased noise and reduced signal reliability.

### **Real-Time Performance Requires Native Implementations**

High-frequency real-time EMG acquisition was impractical in the initial Python implementation due to throughput limitations. Native C++ implementations significantly improved acquisition speed and responsiveness.

These findings help establish design requirements for future acquisition systems and hardware development.

---

# **7. Proposed Future Work**

The next stage of the project focuses on expanding both software and hardware capabilities.

## **Software Expansion**

Future software work includes:

- Graphical experiment control interfaces
- Automated Motor Evoked Potential (MEP) detection
- Real-time filtering and preprocessing
- Integration with stimulation triggers
- Multi-channel acquisition support
- Scalable experiment data management
- Machine learning assisted signal analysis

## **Hardware Development**

Future hardware research includes:

- Custom EMG signal conditioning boards
- Amplification and filtering circuitry
- Electrical isolation and EMI mitigation systems
- Portable acquisition modules
- Battery-powered experimental systems
- Modular multi-channel EMG acquisition hardware
- Integrated filtering and preprocessing hardware

The long-term objective is to create an affordable and extensible open research platform for neuroscience and neuroengineering applications.

---

# **8. Research and Academic Impact**

The proposed work has the potential to contribute significantly to affordable neuroscience research infrastructure.

Potential impact areas include:

- Reduced dependence on proprietary acquisition systems
- Affordable experimental platforms for smaller labs
- Faster and more flexible neuroscience workflows
- Open and reproducible research infrastructure
- Integration with modern data science and machine learning tools
- Support for future neuroengineering and rehabilitation research
- Scalable infrastructure for biomedical signal analysis

The project also provides opportunities for interdisciplinary collaboration between computer science, biomedical engineering, neuroscience, and psychiatry.

---

# **9. Proposed Figures and Diagrams**

The following figures and diagrams should be included in the final proposal document:

- TMS and EMG acquisition overview diagram
- Micro1401 acquisition architecture diagram
- Signal acquisition pipeline flowchart
- Python vs C++ performance comparison graph
- EMI experimental setup photographs
- Signal plots under different noise conditions
- Electrode degradation comparison graphs
- Real-time visualization screenshots
- Prototype implementation screenshots
- Hardware block diagrams
- Experimental setup photographs

---

# **10. Roadmap and Timeline**

## **Phase 1**

Initial low-cost EMG experimentation and signal quality analysis.

## **Phase 2**

Development of Python-based real-time acquisition prototype.

## **Phase 3**

Migration to optimized C++ acquisition pipeline.

## **Phase 4**

Development of modular hardware acquisition and filtering systems.

## **Phase 5**

Integration with advanced neuroscience workflows, automation systems, and analysis pipelines.

---

# **11. Conclusion**

This project demonstrates the feasibility of developing lightweight and extensible EMG acquisition systems for TMS research using open and customizable software and hardware pipelines.

The work successfully validated:

- Real-time EMG acquisition using Micro1401 hardware
- Open-format storage and visualization workflows
- High-performance acquisition using optimized native implementations
- Identification of key practical challenges affecting EMG reliability
- Potential for scalable future neuroengineering research infrastructure

The proposed future expansion into modular hardware systems and advanced signal analysis pipelines can help create affordable, research-friendly, and extensible infrastructure for neuroscience and biomedical engineering applications.

---

# **Appendix: Existing Results Summary**

## **Performance Comparison**

|**Implementation**|**Approximate Throughput**|
|---|---|
|Python Prototype|~1 kSamples/s|
|C++ Implementation|~20 kSamples/s|

## **Key Noise Contributors Identified**

1. Electrical Interference (EMI)
2. Low Power Conditions
3. Electrode Placement Variability
4. Patch Degradation
5. Environmental Noise

---

# **References and Supporting Material**

- Internal experimental reports
- EMG noise analysis studies
- TMS acquisition workflow documentation
- Micro1401 and CED driver documentation
- Real-time acquisition benchmarking results