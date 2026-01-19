## Hand2Hope – Donation Management Mini Project
A web-based donation platform developed as part of the Mini Project (22CDS48) under the Department of Computer Science & Engineering (Data Science).The backend database is used to persist donor and campaign data submitted through the application.



## Project Description
Hand2Hope is a web-based donation application designed to digitize and simplify the donation process. The system allows users to enter donor details, select donation amounts, and submit donations through a clean and intuitive interface.
The project emphasizes usability, transparency, and accessibility, making it suitable for small charitable organizations that lack complex technical resources.

## Problem Statement
Many small NGOs and charitable organizations lack access to affordable and easy-to-use digital donation platforms. Existing systems are often complex and costly, which reduces donor trust and engagement.


## Objectives
- To develop a simple and user-friendly donation platform prototype.
- To demonstrate the core donation workflow using web technologies.
- To analyze limitations of existing donation systems and propose improvements.

## Tech Stack
- Frontend: HTML, CSS, JavaScript
- Backend:  PHP 
- Database: MySQL



## Features
- Donation form for collecting donor details
- Donation amount input
- Basic input validation
- Donation confirmation message
- Simple and responsive UI

## How to Run the Project
1. Clone the repository
2. Import the MySQL database using the provided SQL scripts
3. Configure database connection in the PHP backend
4. Run the project on a local server (XAMPP / WAMP)
5. Access the application via browser and submit the donation form



## Project Scope
This project implements a basic backend for storing donor and campaign-related details in a database. Advanced features such as payment gateway integration, authentication, and large-scale deployment are considered future enhancements.








## 🗂️ Database Design and Implementation
The backend database stores information related to charities, campaigns, donors, and donations. The following tables are used in the system:



###  Charities Table
```sql
CREATE TABLE charities (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    phone VARCHAR(15),
    address TEXT,
    registered_datetime DATETIME DEFAULT CURRENT_TIMESTAMP
);
```

### Campaigns Table

```sql
CREATE TABLE campaigns (
    id INT AUTO_INCREMENT PRIMARY KEY,
    charity_id INT,
    title VARCHAR(100) NOT NULL,
    description TEXT,
    goal_amount DECIMAL(10,2),
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (charity_id) REFERENCES charities(id) ON DELETE CASCADE
);
```

### Donations Table

```sql
CREATE TABLE donations (
    id INT AUTO_INCREMENT PRIMARY KEY,
    donor_id INT,
    campaign_id INT,
    amount DECIMAL(10,2) NOT NULL,
    donated_on DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (donor_id) REFERENCES donors(id) ON DELETE CASCADE,
    FOREIGN KEY (campaign_id) REFERENCES campaigns(id) ON DELETE SET NULL
);
```

### Donation Requests Table

```sql
CREATE TABLE donation_requests (
    id INT AUTO_INCREMENT PRIMARY KEY,
    charity_id INT,
    campaign_id INT,
    description TEXT,
    requested_amount DECIMAL(10,2),
    FOREIGN KEY (charity_id) REFERENCES charities(id),
    FOREIGN KEY (campaign_id) REFERENCES campaigns(id)
);
```
## Academic Context
This project was developed as part of the Mini Project course (22CDS48) for Computer Science & Engineering (Data Science).

## 🖼️ Screenshots
The following screenshots illustrate the user interface and donation workflow of the application.


### Main Page

 ![Main Page](./Screenshots/mainPage.png)
![Main Page 2](./Screenshots/mainPage2.png)

---

### Donor Page

![Donor Page](./Screenshots/donorHome.png)
