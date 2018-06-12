# EMR-IC Connector 1.0 

## Background:
EMR-IC Connector uses two Iguana instances. An on-premises instance that is already in use for Evolve EMR (EMR Iguana) and cloud instance specifically for Evolve IC (IC Iguana).
The solution requires a set of channels and scripts needs to be deployed. 

## Boundaries: 
This guide describes deployment of EMR-IC Connector from a integration developer point of view. 
- Connectivity between EMR and IC Iguana is assumed to be covered as part of infrastructure workstream and subject to separate deployment guide.
- SSO functionality is assumed to be covered as part of infrastructure workstream and subject to separate deployment guide.

## Deployment:

### EMR Iguana:
1. 

### EMR EDC:

### Evolve EMR:

### IC Iguana:
1. Add new channel "Inbound - 1.1 PAS"


Click "Add Channel" in Iguana dashboard.
Specify source as "LLP Listener" and destination as "To Channel"
click "Start Configuring"


On Channel tab check "Start automatically"

On Source tab 
	Set Port to 5400
	Check "Use SSL"
	Add Certificate, Private key, Certificate authority file locations (details should be obtained from DevOps)
	
	Example configuration is shown below:
	




Leave default values for the rest

Click "Add Channel"


2. Add new channel "Inbound - 1.2 PAS to FHIR"


## Script import:


## Supported Iguana versions:

The code has been tested against following Iguana versions: 
* EMR - Iguana 5.5.4
* IC - Iguana 6.0.5
