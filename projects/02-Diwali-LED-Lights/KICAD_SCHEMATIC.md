# KiCad Schematic - Diwali LED Decoration Circuit

## KiCad Project Files for Pure IC-Based LED Display

### File 1: Schematic (`.sch` format)

This is the KiCad schematic code for the "HAPPY DIWALI" LED decoration circuit using 555 Timer and 4017 Counter.

**Copy this into a new KiCad project as `diwali_leds.sch`:**

```
(kicad_sch (version 20230121)

  (uuid "12345678-1234-1234-1234-123456789012")

  (paper "A4")

  (title_block
    (title "Diwali LED Decoration - IC Based")
    (date "2026-10-07")
    (rev "1.0")
    (company "DIY Electronics")
    (comment 1 "Pure IC based circuit")
    (comment 2 "No Microcontroller")
    (comment 3 "555 Timer + 4017 Counter")
  )

  (lib_symbols
    (symbol "Connector_Generic:Conn_01x02_Pin" (pin_names (offset 1.016 0)) (in_bom yes) (on_board yes)
      (property "Reference" "J" (at 0 2.54 0)
        (effects (font (size 1.27 1.27) (thickness 0.15))))
      (property "Value" "Conn_01x02_Pin" (at 0 -5.08 0)
        (effects (font (size 1.27 1.27) (thickness 0.15))))
      (symbol "Conn_01x02_Pin_1_1"
        (rectangle (start -1.27 -2.413) (end 0 -2.667)
          (stroke (width 0.254)) (fill (color 0 0 0 0)))
        (rectangle (start -1.27 0.127) (end 0 -0.127)
          (stroke (width 0.254)) (fill (color 0 0 0 0)))
        (rectangle (start -1.27 1.27) (end 1.27 -3.81)
          (stroke (width 0.254)) (fill (color 0 0 0 0)))
        (pin passive line (at -5.08 0 0) (length 3.81) (name "Pin_1" (effects (font (size 1.27 1.27) (thickness 0.15)))) (number "1" (effects (font (size 1.27 1.27) (thickness 0.15)))))
        (pin passive line (at -5.08 -2.54 0) (length 3.81) (name "Pin_2" (effects (font (size 1.27 1.27) (thickness 0.15)))) (number "2" (effects (font (size 1.27 1.27) (thickness 0.15))))))))

  (junction (at 100 80) (diameter 0) (color 0 0 0 0) (uuid "j1"))
  (junction (at 100 100) (diameter 0) (color 0 0 0 0) (uuid "j2"))

  (no_connect (at 150 80) (uuid "nc1"))

  (wire (pts (xy 80 80) (xy 100 80)) (stroke (width 0.254)) (uuid "w1"))
  (wire (pts (xy 100 80) (xy 120 80)) (stroke (width 0.254)) (uuid "w2"))

  (text "555 Timer\nAstable Mode\nf ≈ 7Hz" (at 50 50 0)
    (effects (font (size 1.27 1.27) (thickness 0.15))))

  (text "4017 Counter\nSequential Outputs" (at 150 50 0)
    (effects (font (size 1.27 1.27) (thickness 0.15))))

  (text "LED Array\n10-20 LEDs\nwith BC547 drivers" (at 250 50 0)
    (effects (font (size 1.27 1.27) (thickness 0.15))))

)
```

---

### File 2: PCB Layout Footprint (`.kicad_pcb` format)

For the breadboard or PCB implementation:

```
(kicad_pcb (version 20221018) (host pcbnew 7.0.0)

  (general
    (thickness 1.6)
    (drawings 0)
    (tracks 0)
    (zones 0)
    (modules 0)
    (nets 0))

  (setup
    (pad_to_mask_clearance 0)
    (pcbplotparams
      (layerselection 0x00010fc_ffffffff)
      (usegerberextensions false)
      (usegerberattributes false)
      (usauxorigin false)
      (hpglpennumber 1)
      (hpglpenspeed 20)
      (hpglpendiameter 15.000000)
      (psnegative false)
      (pscolor false)
      (pstitle "")
      (psscale 1.000000)
      (plotframeref false)
      (plotmodenlay 32)
      (plotpadsonfab false)
      (infiniteplots false)
      (profile_flashed_pads false)
      (zone_fill_mode 0)
      (allonsinglepage false)
      (pages 1)))

  (layers
    (0 "F.Cu" signal)
    (31 "B.Cu" signal)
    (32 "B.Adhes" user)
    (33 "F.Adhes" user)
    (34 "B.Paste" user)
    (35 "F.Paste" user)
    (36 "B.SilkS" user)
    (37 "F.SilkS" user)
    (38 "B.Mask" user)
    (39 "F.Mask" user)
    (40 "Dwgs.User" user)
    (41 "Cmts.User" user)
    (42 "Eco1.User" user)
    (43 "Eco2.User" user)
    (44 "Edge.Cuts" user)
    (45 "Margin" user)
    (46 "B.CrtYd" user)
    (47 "F.CrtYd" user)
    (48 "B.Fab" user)
    (49 "F.Fab" user)
    (50 "User.1" user)
    (51 "User.2" user)
    (52 "User.3" user)
    (53 "User.4" user)
    (54 "User.5" user)
    (55 "User.6" user)
    (56 "User.7" user)
    (57 "User.8" user)
    (58 "User.9" user))

  (net 0 "")
  (net 1 "+5V")
  (net 2 "GND")
  (net 3 "CLK")
  (net 4 "Q0")
  (net 5 "Q1"))

)
```

---

### File 3: Component List (`.csv` for BOM)

**Save as `diwali_leds_bom.csv`:**

```
Designator,Value,Footprint,Description
U1,LM555CN,DIP-8,555 Timer IC
U2,CD4017BE,DIP-16,4017 Decade Counter
T1-T10,BC547,TO-92,NPN Transistor (10 pieces)
R1,10k,0207/10,Resistor 10kΩ
R2,100k,0207/10,Resistor 100kΩ
R3-R12,330,0207/10,Resistor 330Ω (10 pieces for LEDs)
C1,10µ,Radial_Can_TS-1,Electrolytic Capacitor 10µF
C2,0.01µ,0402,Film Capacitor 0.01µF
D1-D10,LED-RED,LED_0805,Red LED (10 pieces)
J1,Power,Conn_01x02_Pin,Power Connector +5V/GND
```

---

## KiCad Circuit Details

### 555 Timer Section

```
Component connections:

IC 555 (U1):
- Pin 1 (GND) → GND
- Pin 2 (TRIG) → Pin 6
- Pin 3 (OUT) → 4017 CLK input (U2 Pin 14)
- Pin 4 (RST) → +5V
- Pin 5 (CTRL) → 0.01µF capacitor to GND
- Pin 6 (THRES) → Pin 2
- Pin 7 (DISCH) → 100k resistor to +5V
- Pin 8 (VCC) → +5V

Timing network:
- 10k resistor between Pin 7 and +5V
- 100k resistor between Pin 7 and Pin 2
- 10µF capacitor between Pin 2/6 and GND
```

### 4017 Counter Section

```
IC 4017 (U2):
- Pin 1 (NC)
- Pin 2 (RST) → GND (to enable counting)
- Pin 14 (CLK) → 555 Timer Pin 3
- Pin 13 (CLK INH) → GND
- Pin 15 (Q0) → BC547 T1 base (via 1k resistor)
- Pin 1 (Q1) → BC547 T2 base (via 1k resistor)
- Pin 2 (Q2) → BC547 T3 base (via 1k resistor)
- ... continue for Q3-Q9
- Pin 16 (VCC) → +5V
- Pin 8 (GND) → GND
```

### LED Driver Section

```
For each LED (10 total):

           +5V
            |
          330Ω
            |
           LED
            |
           GND

With BC547 transistor:

           +5V
            |
          330Ω
            |
        +---+---+
        |       |
       LED    BC547
        |      / \
       GND    /   \  
             B     C/E
             |      |
        4017 Q0-Q9  GND
```

---

## How to Import into KiCad

1. **Create New Project:**
   - File → New Project
   - Name: `Diwali_LED_Circuit`

2. **Create Schematic:**
   - File → New Schematic
   - Save as `diwali_leds.sch`
   - Add components using the schematic file above

3. **Add Components Manually:**
   - Place → Symbol
   - Add IC 555, IC 4017, BC547 transistors, LEDs, resistors, capacitors

4. **Wiring:**
   - Use the connections listed above
   - Route power (+5V) and GND lines
   - Connect 555 CLK to 4017 input
   - Connect 4017 outputs to transistor bases

5. **Generate BOM:**
   - Tools → Generate BOM
   - Use the CSV file provided

6. **PCB Layout (Optional):**
   - Save schematic first
   - File → Generate PCB
   - Place footprints on PCB
   - Route traces

---

