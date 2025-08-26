------

# California Residential Electrical Design and Permit Workflow

## A. Master end to end workflow

```mermaid
flowchart TD
  Z0[Pre design]
  Z1[Load calculation including EV PV ESS per Article 220]
  Z2[Service and panel location and dimensions per 110 26 and 240 24 and 230 85]
  Z3{Need additional panels or feeders}
  Z4[Design subpanels and feeders per 215 and 310 16 and 250 32]
  Z5[Photovoltaic tie in per 705 11 or 705 12 plus rapid shutdown per 690 12]
  Z6[Electric vehicle readiness and EVSE per CALGreen 4 106 4 1 and CEC Article 625]
  Z7[Energy storage location disconnect and listings per CRC R328 and CFC 1206 and CEC 705 and 706]
  Z8[Labels and directories per 230 85 E and 705 10 and 690 56 and 408 4]
  Z9[One line site and elevations and panel schedules]
  ZA[Permit submittal and corrections]
  ZB[Inspections rough to final including labels and protection]

  Z0 --> Z1 --> Z2 --> Z3
  Z3 -- Yes --> Z4 --> Z5
  Z3 -- No --> Z5
  Z5 --> Z6 --> Z7 --> Z8 --> Z9 --> ZA --> ZB
```

------

## B. Service and panel location and dimensions

### B1. Workflow

```mermaid
flowchart TD
  A[Confirm service size from Article 220 demand]
  B[Select service equipment location per 230 70 and 230 85]
  C[Check panel location limits per 240 24]
  D[Verify working clearance per 110 26 A]
  E[Verify dedicated equipment space per 110 26 E]
  F[Verify handle height and accessibility per 240 24 A]
  G[Verify door swing and illumination per 110 26]
  H[Install SPD at service per 230 67]
  I[Provide outdoor emergency disconnect and exact marking per 230 85 E]
  J[Provide intersystem bonding termination per 250 94]
  K[Provide panel directory and multiple sources directory per 408 4 and 705 10]

  A --> B --> C --> D --> E --> F --> G --> H --> I --> J --> K
```

### B2. Quick rules to paste on drawings

| Topic                                 | Requirement                                                  | Code section        |
| ------------------------------------- | ------------------------------------------------------------ | ------------------- |
| Working space                         | Depth 36 in, width 30 in or width of equipment, height 6 ft 6 in | 110.26 A            |
| Door and egress                       | Door in working space opens 90 degrees                       | 110.26 A 2          |
| Illumination                          | Lighting required for the working space                      | 110.26 D            |
| Dedicated equipment space indoor      | Keep foreign systems out above panel to 6 ft above or structural ceiling | 110.26 E 1          |
| Dedicated equipment space outdoor     | Keep foreign systems above clear and protect from precipitation | 110.26 E 3          |
| Prohibited locations                  | No panelboards in bathrooms or clothes closets and not over steps | 240.24 D E F        |
| Handle height and access              | Operating handle at or below 6 ft 7 in and readily accessible | 240.24 A            |
| Outdoor emergency disconnect dwelling | Required and labeled per exact wording                       | 230.85 and 230.85 E |
| SPD at dwelling service               | Type 1 or Type 2 at service equipment                        | 230.67              |
| Intersystem bonding termination       | Provide at service                                           | 250.94              |
| Panel directory                       | Clear and specific circuit identification                    | 408.4 A             |
| Multiple sources directory            | Plaque at service identifying all source disconnect locations | 705.10              |

------

## C. Panel quantity and subpanel decision

### C1. Decision workflow

```mermaid
flowchart TD
  A[Start with demand calculation from Article 220]
  B{Demand exceeds service rating or bus limit}
  C{Circuit count exceeds spaces}
  D{Multi story or long homeruns or voltage drop concerns}
  E{PV or ESS or generator requires segregation or backup loads}
  F[Add subpanel design]
  G[Proceed with single panel]

  A --> B
  B -- Yes --> F
  B -- No --> C
  C -- Yes --> F
  C -- No --> D
  D -- Yes --> F
  D -- No --> E
  E -- Yes --> F
  E -- No --> G
```

### C2. Subpanel design rules

- **Feeder sizing** per Article 215 and ampacity per Table 310.16.
- **OCPD for feeder** per 215.3 and 240.21.
- **Neutral isolated in subpanels** and **bond only at service** per 250.24 A 5.
- **Equipment grounding conductor** with feeder per 250.32 B 1.
- **Detached structure** requires building disconnect per 225.31 and 225.32 and a grounding electrode system per 250.32 A.
- Apply **working space and dedicated space** at every panel per 110.26 and 110.26 E.
- If PV backfeeds a subpanel apply **705.12** in that panel.
- Provide **panel directory** at each panel per 408.4 A and keep **705.10 directory** at service updated.

------

## D. PV integration

### D1. Workflow

```mermaid
flowchart TD
  A[Define inverter AC output current and OCPD]
  B{Choose interconnection method}
  C[Load side interconnection per 705 12]
  D[Supply side interconnection per 705 11]
  E[Load side bus and feeder calculation including 120 percent rule]
  F[Supply side disconnect and OCPD location and tap method]
  G[Provide rapid shutdown and initiator per 690 12]
  H[Provide PV labels including AC output and RSD labels per 690 54 and 690 56 C]
  I[Update multiple sources directory per 705 10]

  A --> B
  B -- Load side --> C --> E --> G
  B -- Supply side --> D --> F --> G
  G --> H --> I
```

**Design checkpoints**

- Load side rule example for a 200 amp bus: main 200 plus PV OCPD must be at or below 240 amps which is one hundred twenty percent of bus. Place PV breaker at the opposite end or per dwelling center fed allowance in 705.12.
- Supply side taps follow 705.11 and 230.46 with disconnect and OCPD outside or first readily accessible point and short conductor length typical ten feet in dwellings.
- Rapid shutdown and labels per 690.12 and 690.56 C.
- Service directory per 705.10 lists all sources and disconnect locations.

------

## E. EV infrastructure

### E1. Workflow

```mermaid
flowchart TD
  A[New one or two family dwelling]
  B[Provide EV capable per CALGreen 4 106 4 1]
  C[Reserve 40 amp 208 240 volt space and raceway to parking]
  D[Mark panel directory EV capable]
  E[Installing EVSE now]
  F[Size branch and OCPD at one hundred twenty five percent continuous load per 625 41 and 210 20]
  G[Provide GFCI where required per 210 8 and AFCI where routing requires per 210 12]
  H[Provide local disconnect if rating above 60 amp or above 150 volt to ground per 625 43]

  A --> B --> C --> D --> E
  E -- Yes --> F --> G --> H
```

**Notes**
 EV receptacles in a garage and outdoors require GFCI per 210.8 A. Many projects choose a hardwired EVSE with integral personnel protection. Keep EV loads in the load calc as continuous.

------

## F. Room by room branch circuits

### F1. Workflow

```mermaid
flowchart TD
  A[Lay out receptacles per 210 52 spacing]
  B[Assign required 20 amp circuits per 210 11 C]
  C[Apply GFCI locations per 210 8 A]
  D[Apply AFCI coverage per 210 12 A]
  E[Update panel schedule and directory per 408 4 A]

  A --> B --> C --> D --> E
```

### F2. Quick table

| Area            | Required circuits                                            | GFCI                                           | AFCI                                                | Other rules                                         |
| --------------- | ------------------------------------------------------------ | ---------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- |
| Kitchen         | Two 20 amp small appliance circuits minimum                  | Yes for countertop and within six feet of sink | Yes                                                 | Spacing per 210.52 C and island and peninsula rules |
| Bathroom        | One 20 amp receptacle circuit dedicated                      | Yes                                            | As routed or per AHJ                                | Receptacle within three feet of basin per 210.52 D  |
| Laundry         | One 20 amp laundry circuit                                   | Yes                                            | Yes                                                 | —                                                   |
| Garage          | One 20 amp circuit for receptacles may also feed exterior receptacles | Yes                                            | Often required by current adoptions verify with AHJ | —                                                   |
| Habitable rooms | Circuits per load calc                                       | Not typically unless near sink                 | Yes                                                 | Spacing per 210.52 A                                |
| Outdoors        | At least one front and one rear receptacle                   | Yes                                            | Not required                                        | 210.52 E                                            |

------

## G. ESS energy storage integration

### G1. Workflow

```mermaid
flowchart TD
  A[Select listed ESS system to UL 9540]
  B[Choose location per CRC R328 and CFC 1206]
  C[Verify clearances and aggregate energy limits]
  D[Provide ESS disconnect and OCPD at exterior or first accessible point]
  E[Integrate with PV or grid per 705 and 706]
  F[Provide signage and update directory per 705 10]
  G[Include manuals listings fire sheets in submittal]

  A --> B --> C --> D --> E --> F --> G
```

**Notes**
 Typical residential limits include location in attached garage or outdoors with clearances and battery energy caps per room. Many AHJs require a heat detector in garages and clear placarding. Keep neutral and grounding rules correct if the system islands through a backup loads panel.

------

## H. Subpanel feeder sizing mini worksheet

Paste this into your E sheets and fill values.

```
Subpanel name: _______________________________
Location: ____________________________________

Load summary for this subpanel:
  General lighting and receptacles VA: __________
  Fixed appliances VA: _________________________
  HVAC VA: ____________________________________
  EVSE VA if landed here: _____________________
  PV backfeed if any: _________________________

Feeder calculations:
  Calculated demand amps at 240 V: ____________
  Continuous load portion amps: _______________
  Multiply continuous by 125 percent: _________
  Non continuous amps: ________________________
  Feeder minimum ampacity total: ______________

Feeder conductors:
  Conductor material and size: ________________
  Insulation type: ____________________________
  Temperature column used from Table 310 16: __
  Adjustments and corrections applied: ________

Overcurrent device at source:
  Rating amps: ________________________________
  Type: _______________________________________

Grounding and bonding:
  Equipment grounding conductor size per 250 122: ______
  Neutral isolated at subpanel yes or no: ______
  Bonding screw removed yes or no: _____________

Working and dedicated space:
  110 26 clearance and 110 26 E dedicated space confirmed
```

------

## I. Detached structure feeder one line and checklist

### I1. ASCII one line diagram

```
Main dwelling service equipment
  Outdoor emergency disconnect per 230 85
  Main service panel with SPD per 230 67

Feeder to detached structure
  Two pole feeder breaker rated ______ A per 215 3
  Feeder conductors ____ AWG material ____ insulation THHN or similar in conduit
  Equipment grounding conductor included with feeder per 250 32 B 1
  Neutral conductor isolated at detached structure panel

Detached structure panel
  Building disconnect per 225 31 and 225 32
  Grounding electrode system per 250 32 A with electrode conductor size ______
  Panel working space per 110 26 and dedicated space per 110 26 E
  Directory per 408 4 A

If PV or ESS located at detached structure
  Apply 705 11 or 705 12 at that structure
  Provide local disconnects and labels and update 705 10 directory at dwelling service
```

### I2. Detached structure checklist

- Feeder sized and protected per 215 and 240.
- Four wire feeder hot hot neutral equipment ground.
- Grounding electrode system at detached building per 250.32 A.
- Building disconnect at detached building per 225.31 and 225.32.
- Neutral isolated and equipment grounding conductor bonded to enclosure at detached panel.
- Working space and dedicated space verified.
- Labeling and directories updated.

------

## J. Label and placard package text

Use these exact texts in your label schedule.

```
Emergency disconnect at dwelling service
  Text line 1: EMERGENCY DISCONNECT
  Text line 2: SERVICE DISCONNECT
  Apply per 230 85 E

If meter disconnect not service equipment
  Text: EMERGENCY DISCONNECT METER DISCONNECT NOT SERVICE EQUIPMENT

Multiple sources directory at service per 705 10
  Text: CAUTION MULTIPLE SOURCES OF POWER
  Include locations of Utility Service Disconnect PV AC Disconnect or backfeed breaker ESS Disconnect
  Include service contact phone

PV AC point of interconnection label per 690 54
  Text: PHOTOVOLTAIC SYSTEM AC POINT OF CONNECTION
  Rated AC output current _____ A  Nominal AC voltage _____ V

Rapid shutdown label per 690 56 C
  Text: PV SYSTEM EQUIPPED WITH RAPID SHUTDOWN
  Instruction to operate the rapid shutdown switch to off
```

------

## K. What to include in the permit set

- Cover sheet with scope summary and the **subpanel feeder worksheet** filled where applicable.
- Site plan and exterior elevations showing **panel and disconnect locations** and **rapid shutdown initiator**.
- One-line diagrams for **utility service**, **PV**, **ESS**, **EVSE** and **detached structures**.
- Panel schedules with **AFCI and GFCI indications** and **directory text**.
- Label schedule using the texts in section J.
- Product cut sheets: PV inverter, ESS system UL 9540, EVSE, SPD.
- Load calculation per Article 220.
- Fire notes for ESS referencing CRC R328 and CFC 1206 where applicable.

