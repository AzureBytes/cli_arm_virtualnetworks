# Creating a Virtual Network and Subnets in Azure using Cross-Platform Command Line Interface and Azure Resource Manager

Configure Your Environment
==========================

Install xPlat CLI
-----------------

1.  Download the cross-platform command line interface (xPlat CLI) pre-compiled installer by using one of the URLs listed below:

    -   **Windows:** <http://aka.ms/webpi-azure-cli>

    -   **Mac:** <http://aka.ms/mac-azure-cli>

    -   **Linux:** <http://aka.ms/linux-azure-cli>

> **Note:** You can optionally use *Node Package* *Manager* to install the interface by installing the *azure-cli* package globally.

Open CLI and Configure for ARM
------------------------------

1.  Open the command-line interface application for your operating system:

    -   **Windows:** Command Prompt

    -   **Mac/Linux:** Terminal

> **Note:** Leave the application open for the remainder of this lab as you will be using it to manage your resources.

1.  Use the following command to enable the **Azure Resource Manager** commands:

                azure config mode arm

Connect to Your Azure Subscription
----------------------------------

1.  Use the **interactive login** to log in to Azure using your enterprise credentials or Microsoft account identity:

                azure login

1.  Open a browser and navigate to <https://aka.ms/devicelogin>. The command prompt will display a device code that you can use to authenticate to Azure.

2.  Once you enter the code, you will be prompted to allow access to the **Microsoft Azure CLI**. Click **Continue**.

3.  Sign in using your identity associated with your Azure subscription.

4.  Once you receive confirmation that you are signed in, you can close your browser window.

Create Your Resources
=====================

Create a Resource Group
-----------------------

1.  Use the following command to list all possible CLI options for **Resource Groups**:

                azure group

1.  Use the following command to create a new resource group with the
    following details:

    -   **Name:** CLITestGroup

    -   **Location:** West US

                azure group create –n “CLITestGroup” –l “West US”

1.  Use the following command to show the details of your resource group:

                azure group show “CLITestGroup”

Create a Virtual Network
------------------------

1.  Use the following command to list all possible CLI options for network components in Azure:

                azure network

1.  Use the following command to list all possible CLI options for **Virtual Networks**:

                azure network vnet

1.  Use the following command to create a new resource group with the following details:

    -   **Name:** CLITestGroup

    -   **Location:** West US

                azure network vnet create –g "CLITestGroup" –n “TestVNET” -l "West US"

1.  View your new virtual network in the list of virtual networks using this command:

                azure network vnet list

1.  View the details of your new virtual network using this command:

                azure network vnet show –g “CLITestGroup” –n “TestVNET”

> **Note:** Notice that some Virtual Network details (such as address prefix) were specified for you. This is because you did not specify any options when using your command. Default options were used.

Create a Subnet
---------------

1.  Use the following command to list all possible CLI options for **Subnets**:

                azure network vnet subnet

1.  Use the following command to create a subnet in your existing Virtual Network with the following options:

                azure network vnet subnet create -g "CLITestGroup" --vnet-name "TestVNET" -n "TestSubnet" --address-prefix 10.0.1.0/24

Create a Network Interface Card 
--------------------------------

1.  Use the following command to list all possible CLI options for **Network Interface Cards**:

                azure network nic

1.  Use the following command to create a Network Interface Card in your resource group with the following options:

                azure network nic create -g "CLITestGroup" -l "West US" -n "TestNIC" --subnet-name "TestSubnet" --subnet-vnet-name "TestVNET"

Clean Up Your Environment
=========================

Remove Resources
----------------

1.  Remove the **CLITestGroup** resource group using the following command:

                azure group delete –n “CLITestGroup”

1.  Close the command line interface application.
