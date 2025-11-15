# Лабораторна робота №1  
**Предметна область:** *Соціальна мережа*  

## ER-моделювання

У межах лабораторної роботи побудовано дві діаграми, які описують структуру даних предметної області: «Соціальна мережа»

---

## 1. Діаграма Чена

![diagram](CHENKPI.drawio.svg)

---

## 2. Діаграма «Воронячі лапки» (Crow’s Foot)

![diagram](CROWKPI.drawio.svg)

## 3. Діаграма в PlantUML 

[Посилання](https://www.planttext.com)

```PlantUML
@startuml

entity User {
  *userId : UUID           // Primary Key
  --
  email : STRING
  password : STRING
  nickname : STRING
  avatarImageUrl: STRING?
  createdAt: DATE
}


entity Post {
  *postId : UUID           // Primary Key
  *userId : UUID           // Foreign Key
  --
  title : STRING
  text : STRING
  imageUrl : STRING
  createdAt: DATE
}

entity Likes {
  *likeId : UUID            // Primary Key
  *postId : UUID           // Foreign Key
  *userId : UUID           // Foreign Key
  --
  createdAt: DATE
}

entity Comment {
  *commentId : UUID           // Primary Key
  *postId : UUID              // Foreign Key
  *userId : UUID              // Foreign Key
  *parentCommentId : UUID?    // Foreign Key
  --
  text: STRING
  createdAt: DATE
}

entity UserFollowers {
  *id : UUID                 // Primary Key
  *followerId : UUID     // Foreign Key
  *followingId : UUID   // Foreign Key
}

entity PostTags {
  *postId : UUID     // Foreign Key
  *tagId : UUID       // Foreign Key
}

entity Tag {
  *tagId : UUID   // Primary Key
  --
  text : STRING 
}

User "1" -- "0..N" Post
User "1" -- "0..N" UserFollowers : followindId
User "1" -- "0..N" UserFollowers : followerId
Post "1" -- "0..N" Likes
User "1" -- "0..N" Likes
Post "1" -- "0..N" Comment
User "1" -- "0..N" Comment
Post "1" -- "0..N" PostTags
Tag "1" -- "0..N" PostTags
Comment "0..1" -- "0..N" Comment : parentCommentId
```

## 4. Відобразити модель у середовищі програмування (Swift)

```swift
class User: Object {
    @Persisted(primaryKey: true) var userId: UUID
    @Persisted var email: String
    @Persisted var password: String
    @Persisted var nickname: String
    @Persisted var userImageUrl: String?
    @Persisted var createdAt: Date
}

class UserFollowers: Object {
    @Persisted(primaryKey: true) var id: UUID
    @Persisted var followerId: UUID
    @Persisted var followingId: UUID
}

class Post: Object {
    @Persisted(primaryKey: true) var postId: UUID
    @Persisted var userId: UUID
    @Persisted var title: String
    @Persisted var text: String
    @Persisted var imageurl: String
    @Persisted var createdAt: Date
}

class PostTags: Object {
    @Persisted var postId: UUID
    @Persisted var tagId: UUID
}

class Tag: Object {
    @Persisted(primaryKey: true) var tagId: UUID
    @Persisted var text: String
}

class Like: Object {
    @Persisted(primaryKey: true) var likeId: UUID
    @Persisted var postId: UUID
    @Persisted var userId: UUID
    @Persisted var createdAt: Date
}

class Comment: Object {
    @Persisted(primaryKey: true) var commentId: UUID
    @Persisted var parentCommentId: UUID?
    @Persisted var text: String
    @Persisted var createdAt: Date
}
```
