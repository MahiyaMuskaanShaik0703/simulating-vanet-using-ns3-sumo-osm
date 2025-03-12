# Real time simulation of VANET using NS3, SUMO and OSM
This project simulates a **Vehicular Ad-hoc Network (VANET)** using **NS3**, **SUMO**, and **OpenStreetMap (OSM)**.  
It helps analyze **Vehicle-to-Vehicle (V2V) and Vehicle-to-Infrastructure (V2I) communication**, focusing on key network performance metrics such as **packet delivery ratio (PDR), packet overhead, and goodput**.  

# TOOLS  
**OS** : Ubuntu 16.04.7 LTS  
**NS** : Version 3.27   
**ECLISPSE SUMO** : Version 1.2  
**OpenStreetMap**(Additional)  

# Key features 
  
**Realistic Traffic Simulation**  
-Makes use of OpenStreetMap (OSM) and SUMO to create realistic road networks.  
  
**Wireless Communication Modeling**  
-Enables communication between vehicles and infrastructure by implementing IEEE 802.11p (WAVE).  
-Supports important VANET routing protocols, including DSDV, AODV, and OLSR.  
  
**Integration of NS3 & SUMO**  
-Realistic vehicle movement is produced using SUMO.  
-Vehicle network connection is simulated by NS3.  
-Uses traceExporter.py to convert mobility data from SUMO to NS3.  
  
**Performance Analysis & Evaluation**  
-Evaluates MAC overhead, latency, throughput, and packet delivery ratio (PDR).  
-Enables comparisons of routing protocols for various traffic scenarios. Using NetAnim for Visualization  
  
**Visualization with NetAnim**  
-Shows packet transmissions and vehicle movement in real time.
  




