# Index
- [Instruct](#instruct)
  - [Query mysql](#query-mysql)
    - [Create database](#create-database)
    - [Database like](#database-like)
  - [Set up connection database](#set-up-connection-database)
  - [Before first run](#before-first-run)
  - [Run](#run)
  - [Edit css by scss (in split terminal)](#edit-css-by-scss-in-split-terminal)
  - [Beauty the code (in split terminal)](#beauty-the-code-in-split-terminal)
  - [Project structure](#project-structure)

# Instruct
# Node js 14.7.0
Correct version required !!!
## Query mysql

Set up mysql in link: [Setup MySQL](https://drive.google.com/file/d/1MjvESVyQR_AgovRXl_KEnkTnpnA7ydRt/view?usp=sharing)

### Create database

```mysql
CREATE DATABASE management_lab_dev;
USE management_lab_dev;

-- Create lab_groups table
CREATE TABLE lab_groups (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    createdAt DATE NOT NULL,
    updatedAt DATE NOT NULL
);

-- Create projects table
CREATE TABLE projects (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    createdAt DATE NOT NULL,
    updatedAt DATE NOT NULL,
    image VARCHAR(255)
);

-- Create students table
CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL,
    labGroupId INT,
    mssv VARCHAR(255),
    createdAt DATE NOT NULL,
    updatedAt DATE NOT NULL,
    description TEXT,
    phoneNumber VARCHAR(20),
    image VARCHAR(255),
    isAdmin TINYINT,
    FOREIGN KEY (labGroupId) REFERENCES lab_groups(id)
);

-- Tạo bảng group_projects
CREATE TABLE group_projects (
    labGroupId INT,
    projectId INT,
    PRIMARY KEY (labGroupId, projectId),
    FOREIGN KEY (labGroupId) REFERENCES lab_groups(id),
    FOREIGN KEY (projectId) REFERENCES projects(id)
);
```
#### Default database (option, no require)
Import each json file in database_each_table to management_lab_dev 

### Database like
![Mô tả ảnh](https://github.com/Quanghusst/Lab-management/blob/main/database%20lab%20management.png)




## Set up connection database
Replace your mysql [username](https://github.com/Quanghusst/Lab-management/blob/main/database%20lab%20management.png) and [password](https://github.com/Quanghusst/Lab-management/blob/main/database%20lab%20management.png)
```javascript
// src/config/database.js
const sequelize = new Sequelize('management_lab_dev', 'username', 'password', {
    host: 'localhost',
    dialect: 'mysql',
    logging: false,
});
```

## Before first run
```bash
npm install 
```

## Run
Type email and mssv and isAdmin in Database
```bash
npm start
```


## Edit css by scss (in split terminal)
```bash
npm run watch
```


## Beauty the code (in split terminal)
```bash
npm run beautiful
```

## Project structure

```txt
│   package.json
│   package-lock.json
│   README.md
├───node_modules
└───src
    │   index.js
    │
    ├───app
    │   ├───controllers
    │   │       AuthController.js
    │   │       GroupsController.js
    │   │       NewsController.js
    │   │       ProjectsController.js
    │   │       SiteController.js
    │   │       StudentsController.js
    │   │
    │   └───models
    │           groupModel.js
    │           groupProjectModel.js
    │           projectModel.js
    │           studentModel.js
    │
    ├───config
    │       database.js
    │
    ├───public
    │   ├───css
    │   │       app.css
    │   │
    │   └───img
    │       │   ico.png
    │       │   ryo_yamada.png
    │       │
    │       ├───projects
    │       │       DESKTOP_CAM.png
    │       │       DESKTOP_TRANG.png
    │       │
    │       └───students
    │               Quang.jpg
    │               ryo_yamada.png
    │
    ├───resources
    │   ├───scss
    │   │       app.scss
    │   │
    │   └───views
    │       │   home.handlebars
    │       │   news.handlebars
    │       │
    │       ├───auth
    │       │       login.handlebars
    │       │
    │       ├───groups
    │       │       create.handlebars
    │       │       details.handlebars
    │       │       edit.handlebars
    │       │
    │       ├───layouts
    │       │       main.handlebars
    │       │
    │       ├───partials
    │       │       footer.handlebars
    │       │       header.handlebars
    │       │       headerUserView.handlebars
    │       │       viewAdmin.handlebars
    │       │       viewUser.handlebars
    │       │
    │       ├───projects
    │       │       create.handlebars
    │       │       details.handlebars
    │       │       edit.handlebars
    │       │
    │       └───students
    │               create.handlebars
    │               details.handlebars
    │               edit.handlebars
    │
    ├───routes
    │       auth.js
    │       groups.js
    │       index.js
    │       news.js
    │       projects.js
    │       site.js
    │       students.js
    │
    └───util
            mysql.js
```

