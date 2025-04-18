# Public-Health-Disease-Surveillance
# Healthcare Data Architecture Development Project

This repository documents a comprehensive architecture development project focused on Electronic Health Records (EHR) and healthcare data interoperability using open-source tools and standards such as OpenEMR, Synthea, HAPI-FHIR, and HL7 FHIR.

## Table of Contents
1. [Virtual Machine Configuration and Testing](#1-virtual-machine-configuration-and-testing)
2. [OpenEMR Installation, Configuration, and Security](#2-openemr-installation-configuration-and-security)
3. [Synthetic Patient and Syndromic Surveillance Data Generation](#3-synthetic-patient-and-syndromic-surveillance-data-generation)
4. [HAPI-FHIR Server Setup](#4-hapi-fhir-server-setup)
5. [FHIR Interoperability and Data Exchange](#5-fhir-interoperability-and-data-exchange)

## 1. Virtual Machine Configuration and Testing

In this phase, virtualized environments were prepared to simulate a secure and scalable hospital information system.

- Platform Used: VirtualBox / VMware / Hyper-V
- Guest OS: Ubuntu Server (22.04 LTS)
- Configuration:
  - 2 CPUs, 4GB RAM, 50GB Storage
  - Static IP Configuration
  - OpenSSH Server for remote access
- Testing:
  - Ping/SSH connectivity verification
  - Basic update/upgrade operations
  - Shared folder access setup (host ↔ VM)

> Purpose: Provides isolated and reproducible environments for deploying the healthcare architecture.

## 2. OpenEMR Installation, Configuration, and Security

OpenEMR is a leading open-source EHR system used to manage medical records, appointments, billing, and more.

- Steps Performed:
  - Installed LAMP stack (Apache, MySQL, PHP)
  - Downloaded and configured latest OpenEMR release
  - Configured HTTPS using self-signed SSL certificates
  - Enabled firewall (UFW) and fail2ban for brute force protection
  - Created user roles and adjusted file permissions for secure access

- Security Measures:
  - MySQL hardening and secure user creation
  - PHP configuration tweaks (e.g., disabling dangerous functions)
  - Periodic backup configuration using `rsync` and `cron`

> Purpose: Establish a secure and functional EHR platform capable of storing and managing healthcare data.

## 3. Synthetic Patient and Syndromic Surveillance Data Generation

Used the Synthea tool to simulate realistic patient data for a hospital system and emulate disease outbreak patterns.

- Tools Used: [Synthea GitHub](https://github.com/synthetichealth/synthea)
- Process:
  - Generated bulk synthetic data in FHIR/CSV/JSON formats
  - Customized modules for specific syndromic conditions (e.g., Influenza, COVID-19)
  - Exported HL7-compatible patient data for integration with OpenEMR and HAPI-FHIR

- Output Data:
  - Demographics
  - Diagnoses and medications
  - Clinical encounters
  - Syndromic surveillance (simulated outbreaks)

> Purpose: Populate systems with realistic test data for evaluating analytics, data exchange, and surveillance.

## 4. HAPI-FHIR Server Setup

HAPI-FHIR is a Java-based open-source implementation of the FHIR standard for healthcare interoperability.

- Setup Overview:
  - Installed Java (OpenJDK 17) and HAPI-FHIR JPA Server
  - Configured PostgreSQL backend for persistence
  - Deployed HAPI-FHIR on Apache Tomcat
  - Enabled RESTful endpoints for FHIR interactions
  - Tested using Postman and cURL with sample FHIR resources

- Security Enhancements:
  - Basic Auth and API token security
  - HTTPS endpoint exposure
  - Database access restrictions

> Purpose: Enables a standards-compliant FHIR server to store and serve clinical data.

## 5. FHIR Interoperability and Data Exchange

This final phase focuses on enabling data exchange between OpenEMR and the HAPI-FHIR server using the FHIR protocol.

- Integrations:
  - Exported patient data from Synthea/OpenEMR in FHIR JSON format
  - Imported FHIR bundles into HAPI-FHIR via REST API
  - Verified data integrity using HAPI-FHIR web UI and FHIR validation tools

- Exchange Operations:
  - `POST /Patient` to create patient data
  - `GET /Patient/{id}` for retrieval
  - `PUT /Observation/{id}` to update clinical data
  - Created automation scripts to bulk push FHIR resources

- Tools Used:
  - Postman for API testing
  - Python scripts with `requests` and `fhir.resources` libraries
  - HAPI-FHIR CLI tools

> Purpose: Demonstrates interoperability and compliance with modern healthcare data standards (HL7 FHIR).

## Final Notes

This architecture simulates a modern, standards-compliant hospital EHR system using open-source tools. It can be expanded to include HL7 v2/v3 integration, real-time analytics, and public health reporting systems.

## Author

Mary Nnipaa Meteku 
mmeteku@mtu.edu

## License

This project is open-source and available under the MIT License.
