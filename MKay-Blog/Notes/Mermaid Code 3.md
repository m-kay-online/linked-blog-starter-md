
flowchart TD
    %% Main Entry Points
    A[Login Page] --> B{Enter Credentials}
    
    %% Login Flow
    B -->|Enter Phone Number| C[Show MR Numbers List]
    C -->|Select Registered MR| D[Auto-fill MR Field]
    D --> E[Enter Password]
    E --> F[Login]
    B -->|Direct MR & Password| F
    C -->|Select Non-Registered MR| G[Signup Page]
    
    %% Signup Flow
    G -->|Enter Phone Number| H[Show Associated MRs]
    G -->|Enter MR Number| I[Verify MR]
    I --> J[Confirmation Modal]
    J --> K[Send OTP]
    K --> L[Enter OTP]
    L --> M[Set Password]
    M --> N[Navigate to Login with MR Pre-filled]
    
    %% Post-Login Flow
    F --> O[Home Screen]
    O --> P[Patient Details]
    O --> Q[Your Reports Card]
    O --> R[Visits & Appointments Card]
    
    %% Reports Flow
    Q --> S[Your Reports Intro Page]
    S -->|View Latest Report| T[Generated Report PDF Page]
    S -->|See All Reports| U[Report Requests Page]
    U -->|Select Request| V[Tests Page]
    V -->|Select Test| T
    
    %% Appointments Flow
    R --> W[Visits & Appointments Page]
    W -->|See Upcoming Appointments| X[Appointments List]
    W -->|View Recent Doctors| Y[Recent Doctors List]
    W -->|See All Previous Visits| Z[Visited Doctors Page]
    Z -->|Select Doctor| AA[Visits by Date Page]
    AA -->|Select Date| AB[Generated Prescription PDF Page]
    
    %% Styling
    classDef primaryScreen fill:#a3cfbb,stroke:#333,stroke-width:2px,color:#333;
    classDef secondaryScreen fill:#c4e0f9,stroke:#333,stroke-width:2px,color:#333;
    classDef action fill:#ffd591,stroke:#333,stroke-width:2px,color:#333;
    classDef pdfPages fill:#ffadad,stroke:#333,stroke-width:2px,color:#333;
    
    class A,G,O,S,U,V,W,Z,AA primaryScreen;
    class C,D,H,I,J,P,X,Y secondaryScreen;
    class B,E,K,L,M,N action;
    class T,AB pdfPages;