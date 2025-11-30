# Лабораторна робота №2 
**Предметна область:** *Соціальна мережа*  

## Use Case Diagram


## 1. Графічний варіант

![diagram](UseCaseDigram.drawio.svg)

---

## 2. Діаграма в PlantUML

![diagram](usecasePlant.png)

## 3. Декларативний опис

```PlantUML
@startuml
actor "Guest user" as Guest
actor "Regular user" as User
actor "Admin" as Admin

usecase "Review Content" as RC
usecase "Like Content" as LC
usecase "Write Comments" as WC
usecase "Follow Others" as FO
usecase "Block Users" as BU
usecase "Delete Content" as DC
usecase "Publish Content" as PC
usecase "Create / Use Tags" as Tags
usecase "Make Registration / Authorization" as Auth
usecase "Delete account" as DA
usecase "Delete content" as DC
usecase "Edit content" as EC
usecase "Make complaint" as MC
usecase "Review complaint" as RCP

Admin --> Auth
Guest --> Auth
Guest --> RC
User --> DA
User --> RC
User --> DC
User --> EC
Admin --> RC
User --> PC
User --> Auth
User --> FO
User --> LC
User --> WC
User --> MC
Admin --> BU
Admin --> DC
Admin --> RCP
BU ..> RCP : <<use>>
DC ..> RC : <<use>>
LC ..> RC : <<use>>
WC ..> RC : <<use>>
FO ..> RC : <<use>>
DC ..> RCP : <<use>>
EC ..> PC : <<use>>
RC ..> PC : <<use>>
MC ..> RC : <<use>>
RCP ..> RC : <<use>>

Tags ..> PC : <<extend>>

@enduml
```
## 4. UseCase + Functional/Nonfunctional req

* UseCase req

- UC1:    Review Content
- UC2:    Like Content  
- UC3:    Write Comments   
- UC4:    Follow Others   
- UC5:    Block Users   
- UC6:    Delete Content   
- UC7:    Publish Content 
- UC8:    Create / Use Tags  
- UC9:    Make Registration / Authorization   
- UC10:   Delete account 
- UC11:   Make complain  
- UC12:   Review complain 
- UC13:   Edit content

* Functional req

- F1: Create account via Google/Apple
- F2: Create account via email + password
- F3: Authorize via email + password
- F4: Authorize via Google/Apple
- F5: Guest can only review content
- F6: Admin can block content
- F7: Admin can review content and complaints
- F8: Admin can block users if they have a 100 complains
- F9: User can make complaint
- F10: Admin can unblock users
- F11: Users can find others
- F12: Users can follow others
- F13: Users can post
- F14: Users can create tags while post
- F15: Users can use tags that already exists
- F16: Users can find posts by tags
- F17: Users can like posts
- F18: Users can write comments and replies
- F19: Users can delete own content
- F20: Users can edit own content
 
* NonFunctional req

- F1: The application shall support Light and Dark modes.
- F2: The application shall automatically follow the system theme unless the user  manually overrides it.
- F3: The application shall support multiple languages (e.g., English + Ukrainian).
- F4: All user-visible text shall be stored in localization files.
- F4: minimum OS version iOS 15, Android 8.0.
- F5: The application shall render correctly on both phones and tablets.
- F6: The application shall support Dynamic Type / Font Scaling.
- F7: The UI shall maintain readable contrast levels in both themes.


## 4. Матриця трасування

### Traceability Matrix (Матриця трасування)

| Use Case / FR               | F1 | F2 | F3 | F4 | F5 | F6 | F7 | F8 | F9 | F10 | F11 | F12 | F13 | F14 | F15 | F16 | F17 | F18 | F19 | F20 |
|-----------------------------|----|----|----|----|----|----|----|----|----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| **UC1 Review Content**      |    |    |    |    | ✅  |    | ✅  |    |    |     |     |     | ✅   |     |     | ✅   |     |     |     |     |
| **UC2 Like Content**        | ✅  | ✅  | ✅  | ✅  |    |    | ✅  | ✅  |    | ✅   |     |     | ✅   |     |     |     | ✅   |     |     |     |
| **UC3 Write Comments**      | ✅  | ✅  | ✅  | ✅  |    |    | ✅  | ✅  |    | ✅   |     |     | ✅   |     |     |     |     | ✅   |     |     |
| **UC4 Follow Others**       | ✅  | ✅  | ✅  | ✅  |    |    |    | ✅  |    | ✅   | ✅   | ✅   |     |     |     |     |     |     |     |     |
| **UC5 Block Users**         | ✅  | ✅  | ✅  | ✅  |    | ✅  | ✅  | ✅  | ✅  | ✅   |     |     | ✅   |     |     |     |     | ✅   |     | ✅   |
| **UC6 Delete Content**      | ✅  | ✅  | ✅  | ✅  |    | ✅  |    |    |    | ✅   |     |     | ✅   |     |     |     |     |     | ✅   | ✅   |
| **UC7 Publish Content**     | ✅  | ✅  | ✅  | ✅  |    | ✅  | ✅  | ✅  |    | ✅   |     |     | ✅   |     |     |     |     |     |     |     |
| **UC8 Create / Use Tags**   | ✅  | ✅  | ✅  | ✅  |    | ✅  | ✅  | ✅  |    | ✅   |     |     | ✅   | ✅   | ✅   |     |     |     |     |     |
| **UC9 Reg / Authorization** | ✅  | ✅  | ✅  | ✅  |    |    |    |    |    |     |     |     |     |     |     |     |     |     |     |     |
| **UC10 Delete Account**     | ✅  | ✅  | ✅  | ✅  |    |    |    | ✅  |    |     |     |     |     |     |     |     |     |     |     |     |
| **UC11 Make Complain**      | ✅  | ✅  | ✅  | ✅  |    |    |    |    | ✅  | ✅   |     |     | ✅   | ✅   | ✅   |     |     | ✅   | ✅   |     |
| **UC12 Review Complain**    | ✅  | ✅  | ✅  | ✅  |    |    | ✅  |    | ✅  |     |     |     | ✅   | ✅   | ✅   |     |     | ✅   | ✅   |     |
| **UC13 Edit Content**       | ✅  | ✅  | ✅  | ✅  |    |    |    | ✅  |    | ✅   |     |     | ✅   |     |     |     |     |     | ✅   | ✅   |

