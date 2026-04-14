# Diagramme d’architecture Modern Workplace Hybride

```mermaid
flowchart TB

    subgraph OnPrem["On-Prem Environment"]
        AD[AD DS<br>Domain Services]
        DNS[DNS / OU / GPO]
        AD --> DNS
    end

    subgraph Hybrid["Hybrid Layer"]
        AADC[Entra Connect<br>(Azure AD Connect)]
    end

    subgraph Cloud["Azure / Cloud"]
        Entra[Entra ID<br>(Azure AD)]
        Intune[Intune / Endpoint Manager]
        Sec[Zero Trust / CA / Defender]
    end

    AD --> AADC
    DNS --> AADC
    AADC --> Entra
    Entra --> Intune
    Intune --> Sec

    Devices[Devices<br>Hybrid Join / Autopilot]
    AADC --> Devices
    Intune --> Devices
