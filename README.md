# PV Trainer Module Data Repository

Welcome to the official PV Trainer module data repository. This repository stores the CSV file used by the PV Trainer app to simulate IV curves and other functionalities related to photovoltaic modules. The CSV contains detailed information about different solar modules and is regularly updated by the community.

Overview

This repository serves as the source for all photovoltaic module data used in the PV Trainer app. The app retrieves this CSV to enable module simulations, IV curve calculations, and more.

If you have a solar module that is not currently listed, feel free to request it to be added.

CSV Structure

The CSV file follows a specific format to ensure compatibility with the app. Each row in the CSV represents one solar module with the following fields:

TABLE

# How to Add a New Module

	1.	Create an Issue: If you want to add a new solar module, create a GitHub Issue in this repository. In your issue, provide the complete details of the module following the format mentioned above.
	2.	Provide Accurate Data: Please ensure that all data is accurate and comes from a reliable source, such as the module’s manufacturer datasheet.
	3.	Review and Approval: Once submitted, the module will be reviewed and, if approved, added to the CSV file.

# How to Report Issues

If you find an error in the module data or have other suggestions, feel free to open an issue in the repository. We will review the reported issue and make corrections if necessary.

# Download the CSV

You can always download the latest version of the module CSV from the repository. This file is continuously updated based on the community’s contributions.

# Example CSV Entry

Here’s an example of how the data should look in the CSV file:
Name,Manufacturer,Technology,Bifacial,STC,PTC,A_c,Length,Width,N_s,I_sc_ref,V_oc_ref,I_mp_ref,V_mp_ref,alpha_sc,beta_oc,T_NOCT,gamma_r,Version
Amerisolar AS-6M-335W,Amerisolar,Mono-c-Si,No,335.0,310.0,1.941,1.956,0.992,72,9.12,45.75,8.66,37.85,0.0046,-0.119,47.5,-0.41,2021

# Contributions

We welcome contributions from anyone who is passionate about solar energy and photovoltaics. Please follow the guidelines provided when adding or modifying module data.

Thank you for helping us improve the PV Trainer app and for supporting solar energy research!

# Let me know if you’d like to modify anything or if you need further assistance.
