# Decentralized-Voting-System-Using-Ethereum-Blockchain

> The Decentralized Voting System utilizing Ethereum Blockchain offers a secure and transparent method for conducting elections. <br>
> By harnessing Ethereum's blockchain technology, this system guarantees tamper-resistant voting records, allowing users to vote remotely while preserving their anonymity and preventing fraudulent activities. <br>
> Discover this cutting-edge project for reliable and decentralized voting procedures.

## Features
-  Utilizes Ethereum blockchain for tamper-proof and transparent voting records.
-  Implements JWT for secure voter authentication and authorization.
-  Intuitive UI for voters to cast votes and view candidate information.
-  Admin panel to manage candidates, set voting dates, and monitor results.
-  Removes the need for intermediaries, ensuring a trustless voting process.

## Requirements
- Node.js 18.14.0
- Metamask
- Python 3.9
- FastAPI
- MySQL Database (running at port 3306)


## Installation

1. Open a terminal.

2. Clone the repository by using the command
```
git clone https://github.com/KushShriv/Decentralised-Voting-System-Solana-JS.git
```

3. Download and install [Ganache](https://trufflesuite.com/ganache/).

4. Create a workspace named <b>developement</b>, in the truffle projects section add `truffle-config.js` by clicking `Add Project` button.

5. Download [Metamask](https://metamask.io/download/) extension for the browser.

6. Now create wallet (if you don't have one), then import accounts from ganache.

7. Add network to the metamask. <br>( Network name - Localhost 7575, RPC URL - http://localhost:7545, Chain ID - 1337, Symbol - ETH)

8. Open MySQL and create database named `voter_db`.
>  NOTE: Don't use Xampp

9. In the database created, create new table named `voters` in the given format and add some values.
``` SQL
CREATE TABLE voters (
voter_id VARCHAR(36) PRIMARY KEY NOT NULL,
role ENUM('admin', 'user') NOT NULL,
password VARCHAR(255) NOT NULL
);
```
```
+----------+------+----------+
| voter_id | role | password |
+-----------------------------
|          |      |          |
+----------+------+----------+
```
10. Set up a `Database_API/.env` file with the following environment variables for the database apis to work properly
```
MYSQL_USER="yourUser"
MYSQL_PASSWORD="yourPassword"
MYSQL_HOST="localhost"
MYSQL_DB="voter_db"
SECRET_KEY= "yourSecretKey"
```
> Set up a `.env` file in the root directory with just the secret key too

11. Install truffle globally
``` 
npm install -g truffle
```

12. Go to the root directory of repo and install node modules
```
npm install
```

13. Install python dependencies
```
pip install fastapi mysql-connector-python pydantic python-dotenv uvicorn uvicorn[standard] PyJWT
```

## Usage

> Note: Update the database credentials in the `./Database_API/.env` file.

1. Open terminal at the project directory

2. Open Ganache and it's `development` workspace.

3. Open terminal in project's root directory and run the command
```
truffle console
```

4. Compile the smart contracts with command
```
compile
```

5. Bundle app.js with browserify
```    
browserify ./src/js/app.js -o ./src/dist/app.bundle.js
```

6. Start the node server server
``` 
node index.js
```

7. Navigate to `Database_API` folder in another terminal
 ```   
cd Database_API
```

8. Start the database server by following command
```
uvicorn main:app --reload --host 127.0.0.1
```

9. In a new terminal migrate the truffle contract to local blockchain
``` 
truffle migrate
```

You're all set! The Voting app should be up and running now at http://localhost:8080/.

## Directory Structure
```
blockchain-voting-dapp            # Root directory of the project.
├── build                         # Directory containing compiled contract artifacts.
|   └── contracts                 
|       ├── Migrations.json       
|       └── Voting.json           
├── contracts                     # Directory containing smart contract source code.
|   ├── 2_deploy_contracts.js     
|   ├── Migrations.sol            
|   └── Voting.sol                
├── Database_API                  # API code for database communication.
|   └── main.py                   
├── migrations                    # Ethereum contract deployment scripts.
|   └── 1_initial_migration.js    
├── node_modules                  # Node.js modules and dependencies.
├── public                        # Public assets like favicon.
|   └── favicon.ico               
├── src                           
|   ├── assets                    # Project images.
|   |   └── eth5.jpg              
|   ├── css                       # CSS stylesheets.
|   |   ├── admin.css             
|   |   ├── index.css             
|   |   └── login.css             
|   ├── dist                      # Compiled JavaScript bundles.
|   |   ├── app.bundle.js         
|   |   └── login.bundle.js       
|   ├── html                      # HTML templates.
|   |   ├── admin.html            
|   |   ├── index.html            
|   |   └── login.html            
|   └── js                        # JavaScript logic files.
|       ├── app.js                
|       └── login.js              
├── index.js                      # Main entry point for Node.js application.
├── package.json                  # Node.js package configuration.
├── package-lock.json             # Lockfile for package dependencies.
├── README.md                     # Project documentation.
└── truffle-config.js             # Truffle configuration file.
```