# Data

The notebook uses two open, labelled datasets. Each record is labelled *normal* or *attack*, and each is treated as one ledger transaction.

| Dataset | Domain | Files | Included here? |
|---|---|---|---|
| **TON_IoT telemetry** (UNSW Canberra) | 7 IoT / IIoT sensors | `Train_Test_IoT_*.csv` | ✅ `data/iot/` |
| **UAVCAN intrusion dataset** (HCRL, Korea University) | Pixhawk 4 UAV, CAN bus, 10 attack scenarios | `type1_label.bin` … `type10_label.bin` | ❌ download, then place in `data/uav/` |

## Getting the UAVCAN files

1. Download the dataset from IEEE DataPort: <https://ieee-dataport.org/documents/uavcan-intrusion-dataset> (DOI [10.21227/fcyc-bb14](https://doi.org/10.21227/fcyc-bb14)). The dataset is described in [arXiv:2212.09268](https://arxiv.org/abs/2212.09268).
2. Copy the ten `typeN_label.bin` files into `data/uav/`.

Expected layout:

```
data/
├── iot/
│   ├── Train_Test_IoT_Fridge.csv
│   ├── Train_Test_IoT_Garage_Door.csv
│   ├── Train_Test_IoT_GPS_Tracker.csv
│   ├── Train_Test_IoT_Modbus.csv
│   ├── Train_Test_IoT_Motion_Light.csv
│   ├── Train_Test_IoT_Thermostat.csv
│   └── Train_Test_IoT_Weather.csv
└── uav/
    ├── type1_label.bin
    ├── ...
    └── type10_label.bin
```

The notebook finds files anywhere under `data/`. On Colab, you can also put every file straight into `/content`.

## Sampling

- **IoT:** 6,000 records per sensor × 7 = 42,000 transactions (59.7% attack)
- **UAV:** 4,200 frames per file × 10 = 42,000 transactions (36.6% attack). Inter-frame timing is computed *before* sampling, so no timing information is lost.

All sampling is seeded (`seed=42`).

## Licences and citation

- **TON_IoT:** free for academic research; commercial use needs permission from the authors. See <https://research.unsw.edu.au/projects/toniot-datasets>, which also lists the papers to cite, including:
  > Alsaedi, A., Moustafa, N., Tari, Z., Mahmood, A. and Anwar, A. (2020) "TON_IoT telemetry dataset: a new generation dataset of IoT and IIoT for data-driven intrusion detection systems", *IEEE Access*, 8, 165130–165150. doi:10.1109/ACCESS.2020.3022862
- **UAVCAN:**
  > Kim, D., Song, Y., Kwon, S., Kim, H., Yoo, J.D. and Kim, H.K. (2022) *UAVCAN intrusion dataset* [Dataset]. IEEE DataPort. doi:10.21227/fcyc-bb14
