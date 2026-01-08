# Experimental Datasets for Manuscript: sensors-4110810

This repository contains the **anonymized and processed datasets** used for the performance evaluation and system verification presented in the manuscript submitted to *Sensors*.

These datasets represent the de-identified workloads used to verify the throughput, latency, and privacy control mechanisms of the proposed scheme.

## Dataset Overview

The repository provides two distinct datasets representing different IoT scenarios:

| Dataset | Type              | Distribution        | Volume (Rows) | Description                                  |
|:------- |:----------------- |:------------------- |:------------- |:-------------------------------------------- |
| **R-1** | Smart Meter       | Right-skew Monetary | ~1.2 Million  | Sparse, LPWAN-style aggregated logs.         |
| **R-2** | Industrial Sensor | Heavy-tailed Usage  | ~8.4 Million  | High-frequency, intensive gateway workloads. |

---

## Detailed Description

### 1. R-1: Smart Meter Data

* **Columns:**
  * `device_id`: Anonymized integer identifier for the smart meter.
  * `timestamp`: Event time of the data reception.
  * `monetary_cost`: The raw scalar value representing accumulated cost.
* **Characteristics:**
  * **Distribution:** **Log-Normal (Right-skew)** 
  * **Temporal Logic:** Exhibits intermittent connectivity and network jitter (randomized arrival intervals), reflecting the "duty-cycled" nature of battery-powered smart meters.
  * **Usage:** Used for verifying **Threshold** judgment operators.

### 2. R-2: Industrial Sensor Data

* **Columns:**
  * `sensor_id`: Anonymized integer identifier for the industrial sensor.
  * `timestamp`: Slotted processing time at the gateway (50ms precision).
  * `usage_value`: The raw usage metric.
* **Characteristics:**
  * **Distribution:** **Heavy-tailed** 
  * **Temporal Logic:** Represents a **slotted aggregated stream**. The precise 50ms intervals reflect the gateway's processing time slots (Batch/Slot aggregation) rather than the transmission time of individual sensors.
  * **Usage:** Used for verifying **Binning (Bucket)** operators and maximum throughput stress testing.

---

## Important Notes on Reproduction

### 1. File Size vs. Record Count

Please note that the **"Size"** column in **Table 3** of the manuscript refers to the **Number of Records** (in **M**illions), not the file size on disk (in MB).

* **R-1:** 1.2M = 1,200,000 records.
* **R-2:** 8.4M = 8,400,000 records.

### 2. Normalization in Figure 3

The datasets provided here contain **raw scalar values** to maintain data integrity.

* **Figure 3** in the manuscript visualizes these distributions after **normalization** for clearer comparative presentation.
* The **bucket overlays** shown in Figure 3 are analytical boundaries applied during the evaluation phase and are not embedded in the raw CSV files.

### 3. Data Privacy

To comply with privacy protocols and confidentiality restrictions regarding the production environment:

* All sensitive identifiers (Geo-location, IP, Serial Numbers) have been removed or hashed.
* The data represents the statistical properties required to reproduce the *experimental trends* (throughput, latency, accuracy).

---

The datasets are provided in CSV format compressed as ZIP archives.

Citation
--------

If you use this dataset, please cite the associated article:

> _Verifiable Differential Privacy Partial Disclosure for IoT with Stateless k-Use Tokens_, Sensors, 2026.
