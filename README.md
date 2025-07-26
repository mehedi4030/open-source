CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    telegram_id VARCHAR(255) UNIQUE,
    name VARCHAR(255),
    balance DECIMAL(10,2) DEFAULT 0,
    total_earned DECIMAL(10,2) DEFAULT 0,
    referred_by VARCHAR(255),
    status ENUM('active', 'banned') DEFAULT 'active',
    join_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE ads (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(255),
    type ENUM('video', 'banner', 'telegram'),
    content TEXT,
    duration INT,
    reward DECIMAL(10,2),
    status ENUM('active', 'inactive') DEFAULT 'active',
    added_on TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE ad_views (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    ad_id INT,
    view_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE withdraw_requests (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    method VARCHAR(100),
    number VARCHAR(100),
    amount DECIMAL(10,2),
    status ENUM('pending', 'approved', 'rejected') DEFAULT 'pending',
    request_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE admins (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(100),
    password VARCHAR(255)
);

CREATE TABLE referrals (
    id INT AUTO_INCREMENT PRIMARY KEY,
    referrer_id INT,
    referred_id INT,
    bonus DECIMAL(10,2),
    referred_on TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
