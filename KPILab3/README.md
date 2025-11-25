# Лабораторна робота №3
**Предметна область:** *Соціальна мережа*  

## Sequence diagram


## 1. Графічний варіант

![diagram](SequenceDiagram.drawio.svg)

---

## 2. Діаграма в PlantUML

![diagram](plantUmlSequence.png)

## 3. Декларативний опис

```PlantUML
@startuml
actor Admin
actor User
participant client
participant server

User -> client: createPostButtonTapped()
activate client
client -> client: checkCameraLibraryAccess()
deactivate client

alt no access
    loop if can't receive access
        client -> User: requestAccess()
        User --> client: completionHandler()
    end
else has access
    client -> User: showLibrary()
    activate client
    User --> client: submitItem()
    client -> User: showFields()
    User --> client: submitFields()
  deactivate client

    opt if user wants to add tag
        User -> client: enterTag()
        activate client
        client -> server: sendRequestToFind()
         activate server
        server --> client: sendSuggestedTags()
        deactivate server
        client --> User: showList()
        User -> client: submit()
        deactivate client
    end
end

User -> client: publishButtonTapped()
activate client
client -> server: sendRequest()
activate server
server --> client: response
client -> User: notification
deactivate client
server -> client: sendPushToAdmin()
activate client
client -> Admin: receivePost()
deactivate client
deactivate server

Admin -> client: reply()
activate client
client -> server: sendReply()
deactivate client
activate server
alt if not approved
server --> client: notification
deactivate server
activate client
client --> User: notification
deactivate client

else approved
    server -> server: store()
    activate server
    deactivate server
    server --> client: notification()
    activate client
    client --> User: notification()
    deactivate client
end

destroy client

@enduml
```
