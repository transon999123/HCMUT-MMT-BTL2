# HCMUT-MMT-BTL2
Main Site Layout (arrange left to right, top to bottom):

Top Area:
[Internet Cloud] --- [ISP Router]

Middle Area (Main Building):
                [Core Router/Firewall]
                        |
        [Distribution Layer 3 Switch]
            /        |         \
    [Access SW] [Access SW] [Access SW]
      /  |  \     /  |  \     /  |  \
    PCs PCs PCs PCs PCs PCs PCs PCs PCs

Right Side Area (DMZ):
[DMZ Switch] --- [Web Server] [DB Server] [Email Server]

Bottom Area (Auxiliary Sites):
[DBP Router] --- [DBP Switch] --- [PCs]
[BHTQ Router] --- [BHTQ Switch] --- [PCs]
```

### **Tips for Clean Layout:**

- **Group related devices together**
- **Leave space between layers** (Core, Distribution, Access)
- **Align devices horizontally/vertically** for clarity
- Use **grid snap** (View → Grid → Snap to Grid)

## **5. Connecting Devices with Cables**

### **Cable Selection:**

1. Click **Connections** (lightning bolt icon)
2. Choose cable type:
   - **Copper Straight-Through** (solid black line) - Switch to PC, Router to Switch
   - **Copper Cross-Over** (dotted line) - Switch to Switch (old devices), PC to PC
   - **Fiber Optic** (yellow line) - Long distance, high speed
   - **Serial DCE/DTE** (clock icon) - WAN connections
   - **Automatic** (lightning) - Packet Tracer chooses for you

### **Connecting Devices:**

1. Click the cable type
2. Click **source device** (e.g., Switch)
3. Select the **port** (e.g., FastEthernet0/1)
4. Click **destination device** (e.g., PC)
5. Select the **port** (e.g., FastEthernet0)
6. Connection appears with colored dots:
   - 🔴 **Red** = Link down/not connected
   - 🟠 **Orange** = Initializing
   - 🟢 **Green** = Link up/working

**Wait a few seconds** for orange dots to turn green!

## **6. Creating Your Hospital Network - Practical Example**

### **Main Site - Building A (Step by Step):**

**Add devices:**
1. Add **1 Router (2911)** - name it "Main-Gateway"
2. Add **1 Layer 3 Switch (3560)** - name it "Core-Switch"
3. Add **3 Layer 2 Switches (2960)** - name them "Floor1-SW", "Floor2-SW", "Floor3-SW"
4. Add **10 PCs** per switch (total 30 PCs)
5. Add **2 Servers** - name them "DHCP-Server", "Web-Server"
6. Add **2 Access Points** for WiFi

**Connect them:**
1. **Router to Core Switch:**
   - Cable: Copper Straight-Through
   - Router port: GigabitEthernet0/0
   - Switch port: GigabitEthernet0/1

2. **Core Switch to Floor Switches:**
   - Cable: Copper Straight-Through or Fiber
   - Core Switch: GigabitEthernet0/2, 0/3, 0/4
   - Floor Switches: GigabitEthernet0/1 each

3. **Floor Switches to PCs:**
   - Cable: Copper Straight-Through
   - Switch: FastEthernet0/1 through 0/10
   - PCs: FastEthernet0

4. **Servers to Core Switch:**
   - Direct connection or through DMZ switch

5. **Access Points to Switches:**
   - Cable: Copper Straight-Through

### **Auxiliary Sites:**

For each site (DBP and BHTQ):
1. Add **1 Router (2911)**
2. Add **1-2 Switches (2960)**
3. Add **10-15 PCs**
4. Add **1 Server**
5. Connect similarly to main site

### **WAN Connection (Between Sites):**

1. **Serial Cable** for WAN simulation:
   - Click **Connections** → **Serial DCE**
   - Connect Main Router Serial0/0/0 to ISP Router Serial0/0/0
   - Click **Serial DTE** 
   - Connect ISP Router to Auxiliary Routers

2. **Or use Copper Cross-Over** for simplicity:
   - Connect routers' GigabitEthernet ports

## **7. Adding Labels and Organization**

### **Add Text Labels:**

1. Click **Miscellaneous** (last icon)
2. Select **Place Note**
3. Click on canvas where you want text
4. Type label (e.g., "Main Site - HCMC", "VLAN 10 - Administration")

### **Add Shapes/Boxes:**

1. Click **Miscellaneous**
2. Select shapes (rectangle, circle)
3. Draw around device groups to show:
   - Different buildings
   - VLANs
   - Security zones (DMZ)

### **Change Colors:**

- Right-click device → **Set Name and Color**
- Use colors to distinguish:
  - Blue = Core layer
  - Green = Distribution
  - Yellow = Access layer
  - Red = DMZ/Servers

## **8. Renaming Devices**

1. Click device
2. Click **Config** tab (GUI) OR
3. Click **CLI** tab and use:
```
   Router(config)#hostname Main-Gateway
```
4. Or just click the label under device and type new name

## **9. Useful Workspace Features**

### **Zoom and Pan:**
- **Zoom in/out**: Mouse wheel or View menu
- **Pan**: Click and drag empty space
- **Fit to window**: View → Zoom → Fit in Window

### **Select Multiple Devices:**
- Click **Select** tool (arrow icon)
- Draw box around multiple devices
- Move them together

### **Delete:**
- Select device
- Press **Delete** key

### **Copy/Paste:**
- Right-click device → **Copy**
- Right-click empty space → **Paste**

## **10. Sample Hospital Network Layout**

Here's how to arrange your hospital network visually:

**Layer 1: Internet & WAN (Top)**
```
[Cloud-Internet] --- [ISP Router] --- [Main Gateway Router]
                          |
                    [DBP Router]  [BHTQ Router]
```

**Layer 2: Core (Main Site - Center)**
```
                  [Firewall/Security]
                          |
                  [Core L3 Switch]
                   /      |      \
```

**Layer 3: Distribution (Below Core)**
```
        [Building A      [Building B      [DMZ
         L3 Switch]       L3 Switch]       Switch]
```

**Layer 4: Access (Bottom)**
```
  [Floor Switches] [Floor Switches]  [Servers]
      |  |  |          |  |  |        |  |  |
    PCs PCs PCs      PCs PCs PCs    Web DB Email
    
  [Access Points for WiFi]
