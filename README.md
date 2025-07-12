# Overview

This project is an automated DHCP registration system built with n8n, running in a self-hosted Docker environment. The workflow allows authorized users to register MAC addresses in the DHCP system through a web form, with automatic IP address assignment and email notifications.

## Features

- User authentication via LDAP  
- MAC address validation  
- Automatic IP address assignment from available pool  
- Email notifications for successful registrations and errors  
- Web forms for user interaction  
- Error handling and user feedback  

## Technical Details

- **Platform**: n8n (self-hosted in Docker)  
- **Authentication**: LDAP integration  
- **DHCP Management**: API calls to external DHCP management system  
- **Email Notifications**: SSH commands to send emails via sendmail  
- **Form Handling**: n8n form nodes for user interaction  

## Installation

1. Ensure you have Docker and Docker Compose installed  
2. Clone this repository  
3. Create a `.env` file with your sensitive configuration (see `.env.example`)  
4. Run `docker-compose up -d`  

## Configuration

The workflow requires the following environment variables:

- `LDAP_AUTH_URL`: LDAP authentication endpoint  
- `DHCP_API_URL`: DHCP management API endpoint  
- `API_TOKEN`: Token for DHCP API access  
- `SSH_CREDENTIALS`: SSH credentials for email notifications  

## Workflow Steps

1. User submits login form with credentials  
2. System authenticates via LDAP  
3. User submits MAC address  
4. System validates MAC format  
5. System queries DHCP server for available IPs  
6. System assigns next available IP  
7. System creates DHCP reservation  
8. Success/error notifications sent via email  
9. User receives confirmation or error message  

## Security Notes

- All sensitive data has been removed from the published workflow  
- Credentials are stored in n8n's credential system, not in the workflow  
- IP addresses and internal URLs have been anonymized  

## License

This project is for internal use only. Contact the maintainers for licensing information.
