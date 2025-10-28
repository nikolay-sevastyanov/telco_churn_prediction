```postgresql
DROP TABLE IF EXISTS telco_customer_status;
CREATE TABLE telco_customer_status (
customer_id varchar PRIMARY KEY,
gender varchar,
senior_citizen integer,
partner varchar,
dependents varchar,
tenure varchar,
churn varchar
);

INSERT INTO telco_customer_status (customer_id, gender, senior_citizen, partner, dependents, tenure, churn)
SELECT customer_id, gender, senior_citizen, partner, dependents, tenure, churn
FROM telco_churn

SELECT * FROM telco_customer_status



DROP TABLE IF EXISTS telco_main_service;
CREATE TABLE telco_main_service (
customer_id varchar NOT NULL,
FOREIGN KEY (customer_id) REFERENCES telco_customer_status(customer_id),
phone_service varchar,
multiple_lines varchar,
internet_service varchar
);

INSERT INTO telco_main_service (customer_id, phone_service, multiple_lines, internet_service)
SELECT customer_id, phone_service, multiple_lines, internet_service
FROM telco_churn

SELECT * FROM telco_main_service



DROP TABLE IF EXISTS telco_misc_services;
CREATE TABLE telco_misc_services (
customer_id varchar NOT NULL,
FOREIGN KEY (customer_id) REFERENCES telco_customer_status(customer_id),
online_security varchar,
online_backup varchar,
device_protection varchar,
tech_support varchar,
streaming_tv varchar,
streaming_movies varchar
);

INSERT INTO telco_misc_services (customer_id, online_security, online_backup, device_protection, tech_support, streaming_tv, streaming_movies)
SELECT customer_id, online_security, online_backup, device_protection, tech_support, streaming_tv, streaming_movies
FROM telco_churn

SELECT * FROM telco_misc_services



DROP TABLE IF EXISTS telco_payment;
CREATE TABLE telco_payment (
customer_id varchar NOT NULL,
FOREIGN KEY (customer_id) REFERENCES telco_customer_status(customer_id),
contract varchar,
paperless_billing varchar,
payment_method varchar,
monthly_chargeS float(2),
total_charges float (2)
);

INSERT INTO telco_payment (customer_id, contract, paperless_billing, payment_method, monthly_charges, total_charges)
SELECT customer_id, contract, paperless_billing, payment_method, monthly_charges, total_charges
```
FROM telco_churn

SELECT * FROM telc
