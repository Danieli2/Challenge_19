# Challenge_19

***
**Background**

I work at a startup that is building a new and disruptive platform called Fintech Finder. Fintech Finder is an application that its customers can use to find fintech professionals from among a list of candidates, hire them, and pay them. As Fintech Finder’s lead developer, I have been tasked with integrating the Ethereum blockchain network into the application in order to enable my customers to instantly pay the fintech professionals whom they hire with cryptocurrency. In this Challenge, I will complete the code that enables your customers to send cryptocurrency payments to fintech professionals. To develop the code and test it out, I will assume the perspective of a Fintech Finder customer who is using the application to find a fintech professional and pay them for their work.

***
**What You're Creating**

To complete this Challenge, you will use two Python files, both of which are contained in the starter folder. The first file that you will use is called fintech_finder.py. 
It contains the code associated with the web interface of your application. I will write all of your code for this Challenge in this file. The second file that I used is called crypto_wallet.py. This file contains the Ethereum transaction functions that you have created throughout this module’s lessons. By using import statements, I integrated the crypto_wallet.py Python script into the Fintech Finder interface program that is found in the fintech_finder.py file. Integrating these two files will allow me to automate the tasks associated with generating a digital wallet, accessing Ethereum account balances, and signing and sending transactions via Ethereum’s Kovan testnet.


Specifically, you will assume the perspective of a Fintech Finder customer in order to do the following:

1. I generate a new Ethereum account instance by using my mnemonic seed phrase.
2. I fetch and display the account balance associated with your Ethereum account address.
3. I calculate the total value of an Ethereum transaction, I included the gas estimate, that pays a Fintech Finder candidate for their work.
4. I digitally signed a transaction that pays a Fintech Finder candidate, and sent this transaction to the Kovan testnet.
5. I reviewed the transactions hash code associated with the validated blockchain transaction.
6. Once I received the transaction’s hash code, I navigated to Kovan’s Etherscan website to review the blockchain transaction details. To confirm that I have successfully created the transaction, I saved screenshots to the README.md file.

***

**Instructions**

The steps for this challenge are broken out into the following sections:

1. Import Ethereum Transaction Functions into the Fintech Finder Application
2. Sign and Execute a Payment Transaction
3. Inspect the Transaction on Etherscan

***

Step 1: 

**Import Ethereum Transaction Functions into the Fintech Finder Application**


In this section, I imported several functions from the crypto_wallet.py script into the file fintech_finder.py, which contains code for Fintech Finder’s customer interface, in order to add wallet operations to the application. 

I complete the following steps:

1. I reviewed the code contained in the crypto_wallet.py script file. 
2. I added my mnemonic seed phrase and your Infura project id (both of which you created earlier in the module) to the starter code’s SAMPLE.env file. 
3. I rename the file .env. 
4. I opened the fintech_finder.py file. 
5. Toward the top of the file, after the imported statements that were provided, I imported the following functions from the crypto_wallet.py file:
      - generate_account
      - get_balance
      - send_transaction
6. Within the Streamlit sidebar section of code, I created a variable named account. 
7. I set this variable equal to a call on the generate_account function. 
8. This function created the Fintech Finder customer HD wallet and Ethereum account. Within this same section of the fintech_finder.py file, I defined a new        st.sidebar.write function that displaied the balance of the customer’s account. Inside this function, I call the get_balance function and pass it to my        Ethereum account.address. 

***

Step 2: 

**Sign and Execute a Payment Transaction**

 I wrote a code that will calculate a fintech professional’s wage, in ether, based on the worker’s hourly rate and the number of hours that they work for a customer.I then wrote code that used the calculated wage value to send a transaction that pays the worker. This code should allow the Fintech Finder customer to authorize the transaction with their digital signature. For the purpose of testing out this application, I used an Ethereum account information as the customer account information. 


To accomplish all of this, I completed the following steps: 

1. The Fintech Finder customers selected a fintech professional from the application interface’s drop-down menu, and then I inputed the amount of time for which they hire the worker. 
2. I wrote the wage variable to the Streamlit sidebar by using st.sidebar.write.
3. The application can calculate a candidate’s wage, I wrote the code that will allow a customer to send an Ethereum blockchain transaction that pays the hired      candidate. To accomplish this, I locate the code that reads if st.sidebar.button("Send Transaction"). I added the logic to this if statement that sends the      appropriate information to the send_transaction function. 
I added the following functionality:
1. The Ethereum account information. From the account instance, the application will be able to access the account.address information that is needed to populate    the from data attribute in the raw transaction.
2. The candidate_address. This will populate the to data attribute in the raw transaction.
3. The wage value. 
4. This will be passed to the toWei function to determine the wei value of the payment in the raw transaction.

***

Step 3:

**Inspect the Transaction on Etherscan**

I test the Fintech Finder application with my newly integrated Ethereum wallet. I sent a test transaction by using the application’s web interface, then I looked up the resulting transaction hash on the Kovan Etherscan block explorer to verify the transactions. 

To do so, I completed the following steps: 

1. From my terminal, I navigated to the project folder that contains my .env file and the fintech_finder.py and crypto_wallet.py files. 
2. To launch the Streamlit application,I typed streamlit run fintech_finder.py.
3. On the resulting webpage, I selected a candidate that I would like to hire from the appropriate drop-down menu. Then,I entered the number of hours that I        would like to hire them for. 

<img width="1439" alt="Screen Shot 2021-11-06 at 7 05 06 PM" src="https://user-images.githubusercontent.com/85910138/140653724-a6aa0eb0-9dda-424a-8d77-ddd1484f1a43.png">



5. I clicked the Send Transaction button to sign and send the transaction with my Ethereum account information. 
6. I then copied my Ethereum address to the Streamlit application page, and navigated to Kovan Etherscan. I pasted my copied Ethereum address into the Kovan        Etherscan search bar.
 Screenshot of My address balance and history on Etherscan: 
 
 <img width="1440" alt="Screen Shot 2021-11-06 at 7 09 18 PM" src="https://user-images.githubusercontent.com/85910138/140653735-cb39b00f-3bba-418e-9a25-869bb0ade408.png">

 <img width="1440" alt="Screen Shot 2021-11-06 at 7 06 49 PM" src="https://user-images.githubusercontent.com/85910138/140653745-b6755004-cdf7-4edb-a2bd-db06ad2e6215.png">

On the Kovan Etherscan page, I clicked on the Txn Hash number associated with the transaction that paid the Fintech Finder candidate.
I took screenshot of the transaction details on Etherscan. 

<img width="1440" alt="Screen Shot 2021-11-06 at 7 07 25 PM" src="https://user-images.githubusercontent.com/85910138/140653772-16a9f597-f295-41ff-8878-14c605404553.png">


<img width="1440" alt="Screen Shot 2021-11-06 at 7 08 22 PM" src="https://user-images.githubusercontent.com/85910138/140653803-f263b788-f05a-4457-89b2-dddae4bfc51a.png">



