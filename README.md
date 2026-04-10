# ParkShare — Agent-Based Simulation Code

**Project:** ParkShare: A Peer-to-Peer Real-Time Parking Exchange Application  
**Author:** Ana  
**Institution:** IE University — Bachelor's Capstone Project (TFG)  

---

## Repository Structure

| Notebook | Description |
|---|---|
| `parkshare_v1.ipynb` | Literature charts + baseline ABM on synthetic 20×20 grid |
| `parkshare_v2.ipynb` | Extended model with sensitivity analysis and statistical testing |
| `parkshare_osm.ipynb` | Robustness validation on the real OSMnx street network of Barrio de Salamanca, Madrid |

---

## How to Run

All notebooks are designed to run on **Google Colab** with no local setup required.

1. Go to [colab.research.google.com](https://colab.research.google.com)
2. Click **File → Upload notebook** and select the `.ipynb` file
3. Run all cells (`Runtime → Run all`)
4. Output files (charts as `.png`, results as `.csv`) appear in the Files panel on the left

Dependencies installed automatically: `osmnx`, `scipy`, `matplotlib`, `pandas`, `numpy`, `networkx`

---

## Simulation Overview

The model simulates a peer-to-peer parking exchange in a high-occupancy urban environment (94% initial occupancy, calibrated to Madrid SER zone peak hours). Drivers arrive via a Poisson process and are assigned as either **app-users** (Finders) or **non-users**, at adoption rates of 0%, 10%, 30%, 60%, and 100%.

Key mechanics:
- **Leaver/Finder dynamic**: a departing driver (Leaver) is matched to an incoming app-user (Finder) within a defined radius before vacating the spot
- **Give-up rate**: drivers who exceed the search time threshold (40 min) abandon the search — this metric is a primary outcome variable
- **30 Monte Carlo runs** per scenario for statistical robustness
- Results validated with Welch's t-tests, 95% CIs, and Cohen's *d* effect sizes

---

## Key Findings

- At 60% app adoption, mean search time falls from ~20 min to ~6.7 min (−66%)
- The give-up rate drops sharply between 0% and 30% adoption, then plateaus — consistent with network externality effects in two-sided marketplaces
- Results are robust across the OSMnx real street network validation (Barrio de Salamanca)

---

## References

- Shoup, D. (2006). Cruising for parking. *Transport Policy*, 13(6), 479–486.
- Hemmatpour, M. et al. (2025). Real-time parking prediction. *ACM SIGSPATIAL*.
- Garrett, J. J. (2011). *The Elements of User Experience*. New Riders.
- Boeing, G. (2017). OSMnx. *Computers, Environment and Urban Systems*, 65, 126–139.
