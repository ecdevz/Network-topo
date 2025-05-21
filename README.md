## Floor-by-Floor Network Topology Diagrams

### 6th Floor - Server Room and Core Infrastructure
```mermaid
graph TB
    subgraph "6th Floor - Server Room"
        %% Internet Connection
        INT((Internet)) --> |1Gbps Primary| FW1[Primary Firewall]
        INT --> |500Mbps Backup| FW2[Backup Firewall]
        
        %% Core Layer
        FW1 --> |10Gbps| CR1[Core Router 1]
        FW2 --> |10Gbps| CR2[Core Router 2]
        CR1 <-->|Redundant Link| CR2
        
        %% Server Farm
        subgraph "Data Center"
            CR1 --> |10Gbps| CS1[Core Switch 1]
            CR2 --> |10Gbps| CS2[Core Switch 2]
            CS1 <--> CS2
            
            CS1 --> |10Gbps| SRV1[App Server Rack]
            CS1 --> |10Gbps| SRV2[DB Server Rack]
            CS2 --> |10Gbps| SRV3[Backup Server Rack]
            CS2 --> |10Gbps| SRV4[Storage Array]
            
            %% Management Network
            CS1 --> |1Gbps| MGMT[Management Network]
            MGMT --> NMS[Network Monitoring]
            MGMT --> IPAM[IP Management]
        end
        
        %% Environmental Monitoring
        CS2 --> ENV[Environmental Controls]
        ENV --> TEMP[Temperature Sensors]
        ENV --> HUM[Humidity Sensors]
        ENV --> PWR[Power Monitoring]
    end
```

### 5th Floor - Training & Conference Rooms
```mermaid
graph TB
    subgraph "5th Floor Infrastructure"
        %% Distribution Switches
        DS1[Distribution Switch 1] --> |1Gbps| F5S1[5F Switch 1]
        DS2[Distribution Switch 2] --> |1Gbps| F5S2[5F Switch 2]
        F5S1 <--> F5S2
        
        %% Conference Rooms
        subgraph "Conference Room 1"
            F5S1 --> VC1[Video Conf System 1]
            F5S1 --> AP1[Wireless AP 1]
            VC1 --> CAM1[Cameras]
            VC1 --> AUD1[Audio System]
        end
        
        subgraph "Conference Room 2"
            F5S1 --> VC2[Video Conf System 2]
            F5S1 --> AP2[Wireless AP 2]
            VC2 --> CAM2[Cameras]
            VC2 --> AUD2[Audio System]
        end
        
        subgraph "Conference Room 3"
            F5S2 --> VC3[Video Conf System 3]
            F5S2 --> AP3[Wireless AP 3]
            VC3 --> CAM3[Cameras]
            VC3 --> AUD3[Audio System]
        end
        
        %% Training Rooms
        subgraph "Training Facilities"
            F5S2 --> TR1[Training Room 1]
            F5S2 --> TR2[Training Room 2]
            F5S2 --> AP4[Wireless AP 4]
            TR1 --> PC1[Training PCs 1-15]
            TR2 --> PC2[Training PCs 16-30]
        end
        
        %% Printers
        F5S1 --> PRN1[Network Printer 1]
        F5S2 --> PRN2[Network Printer 2]
    end
```

### 4th Floor - Executive & Business Consultants
```mermaid
graph TB
    subgraph "4th Floor Infrastructure"
        %% Distribution Switches
        DS1[Distribution Switch 1] --> |1Gbps| F4S1[4F Switch 1]
        DS2[Distribution Switch 2] --> |1Gbps| F4S2[4F Switch 2]
        F4S1 <--> F4S2
        
        %% Executive Area
        subgraph "Executive Wing"
            F4S1 --> EAP1[Exec AP 1]
            F4S1 --> EWS[Executive Workstations]
            EWS --> ES1[Exec Suite 1-10]
            EWS --> ES2[Exec Suite 11-20]
        end
        
        %% Business Consultants Area
        subgraph "Consultants Area"
            F4S2 --> CAP1[Consultants AP 1]
            F4S2 --> CAP2[Consultants AP 2]
            F4S2 --> CWS1[Consultant WS 1-25]
            F4S2 --> CWS2[Consultant WS 26-50]
        end
        
        %% Shared Resources
        F4S1 --> PRN3[Network Printer 3]
        F4S1 --> PRN4[Network Printer 4]
        F4S2 --> PRN5[Network Printer 5]
    end
```

### 3rd Floor - IT & Administrative Staff
```mermaid
graph TB
    subgraph "3rd Floor Infrastructure"
        %% Distribution Switches
        DS1[Distribution Switch 1] --> |1Gbps| F3S1[3F Switch 1]
        DS2[Distribution Switch 2] --> |1Gbps| F3S2[3F Switch 2]
        F3S1 <--> F3S2
        
        %% IT Department
        subgraph "IT Department"
            F3S1 --> ITAP1[IT AP 1]
            F3S1 --> ITWS[IT Workstations]
            ITWS --> ITS1[IT Staff 1-13]
            ITWS --> ITS2[IT Staff 14-25]
            F3S1 --> ILAB[IT Lab Equipment]
        end
        
        %% Admin/HR Area
        subgraph "Admin & HR"
            F3S2 --> AAP1[Admin AP 1]
            F3S2 --> AWS[Admin Workstations]
            AWS --> AS1[Admin Staff 1-13]
            AWS --> AS2[Admin Staff 14-25]
        end
        
        %% Shared Resources
        F3S1 --> PRN6[Network Printer 6]
        F3S2 --> PRN7[Network Printer 7]
        F3S2 --> PRN8[Network Printer 8]
    end
```

### 2nd Floor - General Staff & Support
```mermaid
graph TB
    subgraph "2nd Floor Infrastructure"
        %% Distribution Switches
        DS1[Distribution Switch 1] --> |1Gbps| F2S1[2F Switch 1]
        DS2[Distribution Switch 2] --> |1Gbps| F2S2[2F Switch 2]
        F2S1 <--> F2S2
        
        %% General Staff Area
        subgraph "General Staff Area"
            F2S1 --> GAP1[General AP 1]
            F2S1 --> GAP2[General AP 2]
            F2S1 --> GWS1[General WS 1-10]
            F2S2 --> GWS2[General WS 11-20]
        end
        
        %% Support Services
        subgraph "Support Services"
            F2S2 --> SAP1[Support AP 1]
            F2S2 --> SWS[Support Workstations]
            SWS --> SS1[Support Staff 1-5]
            SWS --> SS2[Support Staff 6-10]
        end
        
        %% Shared Resources
        F2S1 --> PRN9[Network Printer 9]
        F2S2 --> PRN10[Network Printer 10]
    end
```

## Network Specifications Per Floor

### 6th Floor - Server Room
- **Core Network Equipment**:
  - Dual Firewalls (Primary: 1Gbps, Backup: 500Mbps)
  - Redundant Core Routers (10Gbps)
  - Core Switches with 10Gbps uplinks
- **Server Infrastructure**:
  - Application Server Rack
  - Database Server Rack
  - Backup Server Rack
  - Storage Array
- **Management Systems**:
  - Network Monitoring
  - IP Management
  - Environmental Controls

### 5th Floor - Conference Level
- **Network Coverage**:
  - 4 Enterprise APs (One per major area)
  - PoE+ enabled switches
- **Conference Rooms**:
  - Dedicated video conferencing systems
  - HD cameras and audio systems
  - 1Gbps dedicated connections
- **Training Rooms**:
  - 30 Training PCs
  - Dedicated APs
  - 2 Network Printers

### 4th Floor - Executive Level
- **Network Coverage**:
  - 3 Enterprise APs (Executive + Consultant areas)
  - PoE+ enabled switches
- **Executive Wing**:
  - 20 Executive workstations
  - Premium WiFi coverage
  - 3 Network Printers
- **Consultant Area**:
  - 50 Workstations
  - Dual AP coverage

### 3rd Floor - IT & Admin
- **Network Coverage**:
  - 2 Enterprise APs
  - PoE+ enabled switches
- **IT Department**:
  - 25 IT staff workstations
  - Lab equipment connections
  - 3 Network Printers
- **Admin Area**:
  - 25 Administrative workstations
  - Dedicated AP coverage

### 2nd Floor - General Staff
- **Network Coverage**:
  - 3 Enterprise APs
  - PoE+ enabled switches
- **General Staff Area**:
  - 20 Workstations
  - 2 Network Printers
- **Support Services**:
  - 10 Support staff workstations
  - Dedicated AP coverage

## Additional Specifications

### Wireless Networks Per Floor
1. **Corporate SSID**:
   - 802.1x authentication
   - WPA3-Enterprise
   - VLAN segregation per department

2. **Guest SSID**:
   - Portal authentication
   - Rate limited
   - Isolated from corporate network

3. **IoT SSID** (where applicable):
   - Device certificate authentication
   - Restricted network access

### Security Measures
- VLAN segregation per department
- ACLs between VLANs
- NAC for device authentication
- Regular security scans
- Traffic monitoring and analysis

### QoS Implementation
- Voice/Video: Priority queuing
- Business Apps: Guaranteed bandwidth
- General Traffic: Best effort
- Guest Traffic: Rate limited
