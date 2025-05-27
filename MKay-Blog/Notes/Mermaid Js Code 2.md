
%%{init: {'theme': 'default', 'themeVariables': { 
  'background': '#f8f9fa', 
  'primaryColor': '#193864',
  'secondaryColor': '#12bc59',
  'tertiaryColor': '#e9ecef',
  'fontSize': '14px',
  'fontFamily': 'Arial, Helvetica, sans-serif',
  'primaryBorderColor': '#0a1c35',
  'secondaryBorderColor': '#0e9547',
  'tertiaryBorderColor': '#ced4da',
  'lineColor': '#495057',
  'textColor': '#212529'
}}}%%
flowchart TD
    %% Main Entry Points and Sub-Processes
    subgraph "Authentication"
        A["Login Page"] --> B{"Authentication\nMethod"}

        %% Login Flow with direct and phone number paths
        B -->|"Enter Phone Number"| C["Display MR Numbers"]
        C -->|"Select Registered MR"| D["Auto-populate MR Field"]
        D --> E["Password Entry"]
        E --> F["Authentication"]
        B -->|"Direct MR & Password"| F
        
        %% Clear connection to signup
        C -->|"Select Non-Registered MR"| G["Registration Page\n(MRNO pre-populated)"]
        
        %% Signup Flow
        G -->|"Enter Phone Number"| H["Display Associated MRs"]
        G -->|"Enter MR Number"| I["Verification Process"]
        I --> J["Confirmation"]
        J --> K["OTP Delivery"]
        K --> L["OTP Validation"]
        L --> M["Password Creation"]
        
        %% Clear connection back to login with pre-filled data
        M ==>|"Registration Complete"| N["Return to Login\n(MRNO pre-populated)"]
        N ==>|"Auto-populated"| D
        
        %% Back button
        G -.->|"Return"| A
    end

    %% Post-Login Flow
    F ==> O["Dashboard"]
    
    subgraph "Dashboard Components"
        O --> P["Patient Profile"]
        O --> Q["Medical Reports"]
        O --> R["Appointments Management"]
    end

    %% Reports Flow
    subgraph "Reports System"
        Q ==> S["Reports Overview"]
        S -->|"View Selected Report"| T["Report Document\nViewer"]
        S -->|"View All Reports"| U["Report Archive"]
        U -->|"Select Request ID"| V["Test Results"]
        V -->|"Select Test"| T
    end

    %% Appointments Flow
    subgraph "Appointments System"
        R ==> W["Appointments Dashboard"]
        W -->|"Upcoming Appointments"| X["Scheduled Appointments"]
        W -->|"Recent Consultations"| Y["Recent Physicians"]
        W -->|"Medical History"| Z["Physician Directory"]
        Z -->|"Select Physician"| AA["Consultation Timeline"]
        AA -->|"Select Date"| AB["Prescription\nViewer"]
    end

    %% Styling for clarity and professionalism
    classDef primaryScreen fill:#193864,stroke:#0a1c35,stroke-width:2px,color:#ffffff,border-radius:4px;
    classDef secondaryScreen fill:#12bc59,stroke:#0e9547,stroke-width:2px,color:#ffffff,border-radius:4px;
    classDef action fill:#ffffff,stroke:#495057,stroke-width:2px,color:#212529,border-radius:4px;
    classDef pdfPages fill:#6c757d,stroke:#495057,stroke-width:2px,color:#ffffff,border-radius:4px;
    
    %% Apply styles to nodes
    class A,G,O,S,U,V,W,Z,AA primaryScreen;
    class C,D,H,I,J,P,X,Y secondaryScreen;
    class B,E,K,L,M,N action;
    class T,AB pdfPages;
    
    %% Link styling
    linkStyle default stroke:#495057,stroke-width:1.5px;
    linkStyle 10,11 stroke:#495057,stroke-width:1.5px,stroke-dasharray: 5 5;
    linkStyle 16,17 stroke:#193864,stroke-width:2px;
    linkStyle 18,23,28 stroke:#193864,stroke-width:2px;