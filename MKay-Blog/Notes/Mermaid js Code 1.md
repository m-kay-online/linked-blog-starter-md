%%{init: {'theme': 'default', 'themeVariables': { 
  'background': '#f8f9fa', 
  'primaryColor': '#2196F3',
  'secondaryColor': '#4CAF50',
  'tertiaryColor': '#FFC107',
  'fontSize': '16px',
  'fontFamily': 'Arial, sans-serif',
  'primaryBorderColor': '#0D47A1',
  'secondaryBorderColor': '#1B5E20',
  'tertiaryBorderColor': '#FF6F00',
  'lineColor': '#555555',
  'textColor': '#212121'
}}}%%
flowchart TD
    %% Main Entry Points and Sub-Processes
    subgraph "Authentication Flow"
        A["📱 Login Page"] --> B{"🔍 Enter
        Credentials"}

        %% Login Flow with direct and phone number paths
        B -->|"Enter Phone Number"| C["📋 Show MR Numbers List"]
        C -->|"Select Registered MR"| D["🔄 Auto-fill MR Field"]
        D --> E["🔐 Enter Password"]
        E --> F["✅ Login"]
        B -->|"Direct MR & Password"| F
        
        %% Clear connection to signup
        C -->|"Select Non-Registered MR"| G["📝 Signup Page
        (MRNO pre-filled)"]
        
        %% Signup Flow
        G -->|"Enter Phone Number"| H["📋 Show Associated MRs"]
        G -->|"Enter MR Number"| I["🔍 Verify MR"]
        I --> J["✓ Confirmation Modal"]
        J --> K["📱 Send OTP"]
        K --> L["🔢 Enter OTP"]
        L --> M["🔐 Set Password"]
        
        %% Clear connection back to login with pre-filled data
        M ==>|"Account Created"| N["🔄 Navigate to Login
        (MRNO pre-filled)"]
        N ==>|"Auto-populated"| D
        
        %% Back button
        G -.->|"Back"| A
    end

    %% Post-Login Flow
    F ==> O["🏠 Home Screen"]
    
    subgraph "Home Screen Options"
        O --> P["👤 Patient Details"]
        O --> Q["📄 Your Reports Card"]
        O --> R["🗓️ Visits & Appointments Card"]
    end

    %% Reports Flow
    subgraph "Reports Management"
        Q ==> S["📊 Your Reports Intro Page"]
        S -->|"View Latest Report"| T["📑 Generated Report
        PDF Page"]
        S -->|"See All Reports"| U["📁 Report Requests Page"]
        U -->|"Select Request"| V["🧪 Tests Page"]
        V -->|"Select Test"| T
    end

    %% Appointments Flow
    subgraph "Appointments Management"
        R ==> W["🏥 Visits & Appointments Page"]
        W -->|"See Upcoming"| X["📅 Appointments List"]
        W -->|"View Recent"| Y["👨‍⚕️ Recent Doctors List"]
        W -->|"See All Previous"| Z["👩‍⚕️ Visited Doctors Page"]
        Z -->|"Select Doctor"| AA["📆 Visits by Date Page"]
        AA -->|"Select Date"| AB["📝 Generated 
        Prescription PDF"]
    end

    %% Styling for clarity and professionalism
    classDef primaryScreen fill:#2196F3,stroke:#0D47A1,stroke-width:3px,color:#fff,border-radius:8px;
    classDef secondaryScreen fill:#4CAF50,stroke:#1B5E20,stroke-width:3px,color:#fff,border-radius:8px;
    classDef action fill:#FFC107,stroke:#FF6F00,stroke-width:3px,color:#212121,border-radius:8px;
    classDef pdfPages fill:#FF5722,stroke:#BF360C,stroke-width:3px,color:#fff,border-radius:8px;
    
    %% Apply styles to nodes
    class A,G,O,S,U,V,W,Z,AA primaryScreen;
    class C,D,H,I,J,P,X,Y secondaryScreen;
    class B,E,K,L,M,N action;
    class T,AB pdfPages;
    
    %% Link styling
    linkStyle default stroke:#555,stroke-width:2px;
    linkStyle 10,11 stroke:#FF6F00,stroke-width:3px,stroke-dasharray: 5 5;
    linkStyle 16,17 stroke:#0D47A1,stroke-width:3px;
    linkStyle 18,23,28 stroke:#0D47A1,stroke-width:3px;