# Blockchain-Based Electronic Health Record (EHR) System

## Overview

This project implements a secure and transparent Electronic Health Record (EHR) system leveraging blockchain technology. By utilizing a decentralized ledger, we aim to enhance data integrity, patient privacy, and interoperability within the healthcare ecosystem. This system includes a frontend for user interaction, a potential Python backend for server-side logic, and Solidity smart contracts to manage and secure health records on the blockchain.

## Key Features

* **Secure Record Storage:** Patient health records are securely stored and linked on the blockchain, ensuring immutability and tamper-resistance.
* **Patient-Centric Control:** Patients have greater control over their health data, potentially managing access permissions for different healthcare providers.
* **Enhanced Data Integrity:** The distributed and cryptographic nature of blockchain ensures the integrity and authenticity of medical records.
* **Improved Interoperability:** Blockchain can facilitate seamless and secure sharing of health information between authorized entities.

## Blockchain Integration

The blockchain component of this EHR system is built using Solidity and managed with Hardhat.

* **Smart Contracts (`contracts/EHR.sol`):** These smart contracts define the core logic for:
    * Storing patient record metadata (e.g., hashes of records stored off-chain, access control information).
    * Managing patient and provider identities on the blockchain.
    * Handling permissions for accessing and updating records.
    * Implementing audit trails of record access and modifications.
* **Off-Chain Storage:** Due to the limitations and cost of storing large files directly on the blockchain, actual medical records (e.g., documents, images) are likely stored off-chain (e.g., using decentralized storage like IPFS or secure cloud storage). The smart contracts store cryptographic hashes of these off-chain records to ensure their integrity and link them to the blockchain.

## Frontend (`website/`)

The frontend, located in the `website/` directory, provides a user interface for patients and healthcare providers to interact with the EHR system. It is built using HTML, CSS, and likely JavaScript.

* **Patient Interface:** Allows patients to:
    * View their medical records.
    * Manage access permissions for providers.
* **Provider Interface:** Enables healthcare providers to:
    * View patient records they have permission to access.
    * Potentially add or update patient records (subject to access controls).
* **Technology Stack:** This frontend likely utilizes:
    * HTML for structuring the content.
    * CSS for styling.
    * JavaScript for dynamic functionality and interaction with the backend and blockchain.

## Python Backend (`app.py`)

The `app.py` file suggests a potential Python backend for this system. This backend might handle tasks such as:

* **API Endpoints:** Providing APIs for the frontend to interact with the blockchain and off-chain storage.
* **User Authentication and Authorization:** Managing user logins and ensuring only authorized users can perform specific actions.
* **Data Processing:** Handling any necessary data transformations or processing before interacting with the blockchain or storing data off-chain.
* **Integration with other services:** Potentially connecting to existing healthcare systems or APIs.
* **Framework:** This backend might be built using frameworks like Flask or Django.

## Setup and Running Instructions

### Prerequisites

Ensure you have the following installed on your system:

* **Node.js and npm (or yarn):** Required for frontend development and potentially Hardhat.
* **Python 3.x:** Required for the backend.
* **pip (Python package installer):** Usually comes with Python.
* **Hardhat:** A development environment for Ethereum smart contracts.
    ```bash
    npm install -g hardhat
    ```

### Steps

1.  **Clone the Repository:**
    ```bash
    git clone <repository_url>
    cd <repository_name>
    ```

2.  **Set up the Smart Contracts:**
    ```bash
    cd my-solidity 
    npm install   
    npx hardhat compile
    npx hardhat node &
    npx hardhat deploy --network localhost
    # Note down the deployed contract addresses, you might need them for the backend/frontend.
    ```

3.  **Set up the Python Backend (if applicable):**
    ```bash
    cd ..
    pip install -r requirements.txt
    # Configure environment variables (if any) in a .env file.
    python app.py 
    # Note down the backend API URL and port.
    ```

4.  **Set up the Frontend:**
    ```bash
    cd website
    npm install   
    # Configure API endpoints and contract addresses in the frontend code (e.g., in a config file).
    npm start  
    # The frontend will likely be accessible at a specific URL (e.g., http://localhost:3000).
    ```

## Usage

1.  **Ensure all components (blockchain node, backend, frontend) are running.**
2.  **Open the frontend application in your web browser.**
3.  **Follow the on-screen instructions to interact with the EHR system.**
    * **Patient Actions:** Add_Recorrd, View_Record, Authorize_Provider, Revoke_Provider
    * **Provider Actions:** View_Record

## Dependencies

### Smart Contracts (`my-solidity/` or `contracts/`)

* Solidity compiler (`solc`)
* Hardhat development environment
* `@openzeppelin/contracts`

### Python Backend (`app.py`)

* Python 3.x
* `requirements.txt` (contains a list of Python libraries, including likely candidates like):
    * Flask or Django (if using a web framework)
    * Web3.py (for interacting with the Ethereum blockchain)
    * python-dotenv (for managing environment variables)

### Frontend (`website/`)

* Node.js
* npm or yarn


## Important Notes, Limitations, and Security Considerations

**Security is paramount for an EHR system. Please be aware of the following:**

* **This is a development project and may not be suitable for production use without rigorous security audits and testing.**
* **Data Privacy:** Ensure compliance with relevant healthcare data privacy regulations (e.g., HIPAA, GDPR). This project aims to enhance privacy through blockchain, but careful implementation is crucial.
* **Off-Chain Data Security:** The security of off-chain data storage is critical. Implement robust encryption and access controls for any data stored off the blockchain.
* **Smart Contract Security:** Smart contracts are immutable once deployed. Thorough auditing for vulnerabilities is essential.
* **Access Control Mechanisms:** Carefully design and implement access control mechanisms in both the smart contracts and the backend to ensure only authorized users can access and modify patient data.
* **Gas Costs:** Interactions with the blockchain (writing data, changing permissions) incur gas costs. Consider optimizing smart contract logic to minimize these costs.
* **Scalability:** Blockchain scalability can be a challenge. Explore potential scaling solutions if the system is intended for a large number of users.

## License

[Specify the license under which your project is released. For example:]

This project is licensed under the [MIT License](LICENSE). See the `LICENSE` file for more information.
