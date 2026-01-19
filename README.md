**#Hand2Hope – Donation Management Mini Project**
A web-based donation platform prototype developed as part of the Mini Project (22CDS48) under the Department of Computer Science & Engineering (Data Science).


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
- HTML
- CSS
- JavaScript


## Features
- Donation form for collecting donor details
- Donation amount input
- Basic input validation
- Donation confirmation message
- Simple and responsive UI

## How to Run the Project
1. Clone the repository
2. Open the project folder
3. Open `index.html` in a web browser
4. Fill in the donation form and submit


## Project Scope
This project is a frontend prototype developed for academic purposes. Backend processing, payment gateway integration, and database storage are considered future enhancements.






## 🗂️ Database Configuration

To support the functionality of this system, the following tables should be created:


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

## 🖼️ Screenshots

### Main Page

 ![Main Page](./Screenshots/mainPage.png)
![Main Page 2](./Screenshots/mainPage2.png)

---

### Donor Page

![Donor Page](./Screenshots/donorHome.png)
