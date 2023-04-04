---
date_created: 2023-03-06
tags: research,
category: research papers
topics: data storage
---
# Summarizing how healthcare data can improve with ZK Proofs and Re-encryption
#research #zkproofs

## Resources
Connected Papers Origin:
https://www.connectedpapers.com/main/be67f5374b0452238c104a1e9b1250a52c418ecb/Blockchain%20based-Interoperable-Healthcare-using-Zero%20Knowledge-Proofs-and-Proxy-Re%20Encryption/graph

PDF Link:
https://www.iitp.ac.in/~halder/Papers/Conference/COMSNET_2020.pdf

Fileverse's IPFS hash of this paper:
https://beta.fileverse.io/files/1bc90189-218c-4699-ba61-50ca047136d8?tab=chat

## Summary

**Problem:**
Electronic healthcare in its current stage does not offer a transparent database for the general public and healthcare companies to interact with and regulations are one of the largest inhibitors for this level of transparency. Instead of interoperable databases, this industry uses service providers that act as intermediaries for storing and accessing medical data. Each of these service providers store this data in locked up silos, all with various levels of security. This limits the overall background of each patient and allows for potential data breaches when it comes to encrypting and decrypting patient information.

**Solution:**
The primary focus of this paper is to display a unified data schema that is fully accessible to any individual, while being able to manage funds, access controls, and permissions between the Healthcare industry and their clients. The end goal is to create a national healthcare framework for the Indian Government's health coverage plan for families underneath the poverty line.

The technology that this framework plans to apply is the [Inter Planetary File System](https://docs.ipfs.tech/concepts/what-is-ipfs/#defining-ipfs) (IPFS), an integration of zero-knowledge proofs using [ZkSnarks](https://consensys.net/blog/developers/introduction-to-zk-snarks/), and individual smart contracts for storing healthcare data and encrypting access to each patient. The innovations provided here include a novel method for authenticating the identity of each patient and implementing passphrases for providing access to the medical data to the hospital. The end user will only have to interact with their Electronic Health Record (EHR) through a "smart card" which contains the encryption for their medical data to provide access to their chosen hospital.

## Introduction

The inspiration behind this paper originated from the worlds' interest in adopting emerging technologies and how cloud based storage has allow for improvements in monitoring vital signs in patients and potential outbreaks. There are multiple regulatory bodies like the HIPAA and GDPR that are adamant on securing medical data.

Health insurance is another major issue as this usually deals with third party services that will then have to access hospital data to validate insurance claims. On the other side of the world, medical conditions in India are closed off to millions below the poverty line and required a government solution to this problem. This solution will need a pricing mechanism and method for securing this data.

To achieve these goals, blockchain-based solutions have been created and adopted to build out privacy integrations for Electronic Health Records (EHRs) in a way that this technology can be used as a digital ledger between hospitals, governments, and their clients/patients. The authors cover IBM's findings that 56% of healthcare institutes plan to adopt blockchain technology. The desire for this technological advancement is there, however its integration with the global healthcare industry still requires increased testing and improvement.

Their goal with this paper is to establish a system that allows for:
- automated insurance claim
- interoperability and data sharing between healthcare providers
- a data schema that can mange:
	- funds
	- access control
	- and permissions
- protecting privacy of medical data

### Contributions

Their framework uses IPFS and smart contract storage combined with a proxy cloud server for managing re-encryption. This allows for delegating access to service providers.

The zero-knowledge proofs they use are applied for verifying patient identities, based around ZkSnarks. This involves a six-digit pin code/passphrase used with a one-way hashing function. This follows with a security analysis of their solution.

## Related Works

There are previous solutions that had been established with a centralized "EHR manager". The authors explain that these previous examples are not suitable for India's healthcare. These cloud-based solutions are more akin to the centralized entities of today and would allow for plain data to be open to any outside risks.

A different example from Saudi Arabia relied on a central Trusted Health Authority, which places a large security risk on a single source or attack vector for the decryption keys.

Finally, the authors cover how blockchain tech had been used in distributed data storage but was limited by their lack of scalability. These concepts led to data replication to occur and would benefit from a paperless EHR system. Their inspiration came from an idea around "e-passport based zk-proofs" so that they can establish a proof of identity for healthcare.

## Preliminaries

#### Blockchain

The authors first begin by explaining the beginning of Bitcoin and how peer to peer (P2P) transactions are an important innovation over the current intermediary system that technology is accustomed to. The main concept to focus on is that the ability to use a distributed ledger for storing and verifying transactions is an immensely powerful tool for our society's systems.

The open-source software built on top of this ledger-based technology uses Smart Contracts and is how this framework will operate for each patient's EHR. 

#### Proxy Re-encryption

For each entity to gain access to these records without revealing this data to everyone, the framework uses public key encryption that transforms this text from one public key to another. The goal is to provide this [proxy encryption](https://link.springer.com/chapter/10.1007/978-3-642-00862-7_19) with as little information as possible for it to perform this transformation.

These are the current definitions you should know regarding Re-encryption:

Definition 1: Any proxy re-encryption scheme can be described by 5 algorithms (KeyGen, ReKeyGen, ReEnc, Enc, and Dec) as follows: 
1) KeyGen(n): This algorithm generates a random public-private key pair. This is most easily referenced by the public key<>private key interaction that blockchain networks provide to users for securing their assets.
2) ReKeyGen(pkA,skA,pkB,sk∗ B): With KeyGen, comes the re-encryption key necessary for the Proxy to convert that information between both parties. This key provides the necessary information from one public key (A) to the other (B). The symbol  * explains that the private key for B may not be necessary to translate this text depending on the algorithm.
3) ReEnc(rencKA−>B,CA): This algorithm is what the re-encryption key executes to convert the necessary text from one public key to another. This text can then be decrypted by the private key of B (skB).
4) Enc(data,pkA): This generates the cipher text from the public key of A that can be decrypted by the private key of A (skA). 
5) Dec(CA,skA): Finally, this decrypts the encrypted cipher text to reveal this data.

#### Zero Knowledge Proofs Example

The implementation of zero knowledge proofs here answers the following question from Goldwasser:
> “How much knowledge needs to be conveyed to show proof of some knowledge?”

The basic understanding of this is a verification method between a "prover" that proves knowledge of the witness to the "verifier" without revealing the actual witness itself.

**Requirements**
1) Completeness: This property relies on the prover and verifier behaving honestly; if true, the ZK Proof will work.
2) Soundness: This property explains that the prover can not generate "false proofs" without knowledge of the witness. 
3) Zero-knowledge: The main requirement of this is that zero knowledge (hence the term) is revealed about the prover to the verifier; all that is needed is the knowledge of this proof being true or false.

These requirements are explained to be present in ZK-snarks, where the authors described a library that provides an example of this method using a similar language as Python. Their reference is:
“Zokrates-scalable privacy-preserving off-chain computations,” in 2018 IEEE International Conference on Internet of Things (iThings).

Throughout the paper, these symbols will be used to explain each Smart Contract and Zero Knowledge Proof applied to their findings:
| Contract     | Symbol | Functionality                                                      |
| ------------ | ------ | ------------------------------------------------------------------ |
| Registration | RSC    | Stores mapping of empanelled hospitals and Beneficiaries           |
| Insurance    | ISC    | Stores remaining balance, EHR hash, PRE Keys and logs audit claims |
| Verifier     | VSC    | Automatically generated by Zokrates to check proofs on chain       |

#### PM-JAY Scheme

The PM-JAY scheme is the Indian Government's healthcare framework for nation health insurance to 100 million families in India. The governement will provide a fund of 2k Crore rupees and 5 Lakh rupees for each family. There are 1,350 medical procedures covered that will have no out of pocket payment needed.

### Proposed System

#### Stakeholders

This explains how the system can help the government and other beneficiaries:

#### Registration of beneficiaries

This example covers 256 bit schemes similar to the already established AES 256 system by the National Institute of Health.

##### Beneficiary Diagram
![](Pasted%20image%2020230306134600.png)
1) The beneficiary uses biometric verification for identification of the individual against his/her national identity or state issued identity such as UIDAI Aadhar, family card to prove identity at registration desk. 
2) The registration manager queries the latest SECC (Socio Economic Caste Consensus) database to check eligibility for coverage under PM-JAY after verifying the identity of beneficiary. 
3) The beneficiary decides a six digits pin (any number of his/her choice) which will act as passphrase for authentication. This six digit pin along with hash of their national ID are used to generate a public private key pair for the beneficiary. An E-card with a private key will be issued to the beneficiary. This process needs to be deterministic to ensure only one unique key pair may be generated for each beneficiary and it needs to be recovered in case E-card is lost. pk,sk = KGen(KDF(pin,hash(NationalID))). 
	1) This applies the "KeyGen" definition from earlier where 'n' is replaced with the pin code and hash of the National ID.
	2) The Password-Based Key Derivation Function 2 (PBKDF2) is a password based key derivation function (KDF) recommended by IETF (Internet Engineering Task Force). 
4) The registration manager will register this pkas a beneficiary in the RSC, setting it’s balance as the insurance coverage (5 Lakh) in ISC and causing an event to be triggered. It will also store a passwordHash along with his public key which will act as authentication mechanism, where PasswordHash = H(sk||pin). This PasswordHash is stored in the VSC and will come into play when we use zero knowledge proofs for authentication later. 
5) The registration manager will generate an unique symmetric key (SYMK) using entropy in the form of public key of beneficiary, e.g. salt, passphrase etc. and encrypt it using beneficiary’s pkbefore uploading to Proxy Reencryption cloud server: CSYMK← Enc (pk, SYMK ), and upload encrypted cipher text to cloud. 
6) A smart card will be issued to the beneficiary with his newly generated public/private key pair stored on board.

This will then cover 15k+ hospitals and provide full coverage for sharing medical EHRs.

#### Zk-Snark Trusted Setup

They need a trusted setup phase to generate the common reference string for generating proofs. The Verifier Smart Contract will also use this to verify said proofs. This uses Zcash as a primary example of what is required.

#### Insurance Claim and Data Sharing

This covers how their approach provides more transparency and convenience for data access and automating insurance claims.

##### Flow diagram for EHR access

![](Pasted%20image%2020230307124247.png)

1) The beneficiary will visit one of 15,000+ empanelled hospitals and present the smart card issued to him along with the six digit pin code decided by him/her during registration. 
2) The hospital uses the pk present on the smart card to generate re-encryption key rencKbeneficiary−>Hospital. The hospital will then act as a prover and compute the proof of private key ownership and knowledge of pre-image of a hash i.e. the PasswordHash using pin and pk. This PasswordHash is cross checked against the one stored in ISC by the VSC. Hospital calls VerifyTX of VSC with the proof created and the re-encryption key as arguments to initiate this cross-checking. 
3) If the proof evaluates as “accept” in VSC the re-encryption key will be added to the mapping of the beneficiary in ISC. This will trigger an event which can be listened to by the cloud and government auditors. 
4) The hospital will now have to fetch data stored on IPFS by checking the hashes of EHRs in the ISC. 
5) Using these hashes, the hospital will use IPFS gateway to fetch the encrypted EHRs. These EHR files will be all encrypted by a symmetric key (SYMK) unique to the patient. 
6) The hospital signs a token with their private key to send a request for patient data access to Cloud proxy re-encryption server. 
7) The cloud server will check whether a re-encryption key exists on the ISC. If so, it will re-encrypt the symmetric key cipher text for the hospitals public key and send it to the hospital. Ci SYMK ←ReEnc(rencKBeneficiary−>Hospital, CSYMK) 
8) The hospital will decrypt the received cipher text from the cloud using it’s private key and use the obtained Symmetric key to decrypt all the associated encrypted files it has fetched from IPFS and use it to gain better insights for patient treatment.

#### Health Insurance Claim

1) Once the empanelled hospital has treated the patient for one of the 1350 procedures covered by PM-JAY a new EHR will be generated by them. 
2) This EHR will be Symmetrically encrypted using the unique SYMK associated for the beneficiary and uploaded to IPFS.
3) The hash of the encrypted EHR along with Public Key of the beneficiary and procedure will be uploaded to the ISC causing an event to be triggered. 
4) This event will be logged to all the stakeholders including the federal government which will monitor for fraudulent activity on the blockchain. 
5) The balance of the beneficiary will be deducted according to the treatment specified and the equivalent amount will be added to the hospital’s balance on the health Insurance smart contract. 
6) Federal government monitors for any fraudulent activity being performed by the empanelled hospital it can ask them to present the decrypted EHRs as proof of treatment.

### Experimental Results

#### Fig 3 - Verifying Proofs

The authors explain that even with 50 consecutive registrations occurring, the proofs generated and verified would take less than six minutes. This is potentially ideal for a single hospital system but would be a crutch on the scalability of this type of program when considering larger countries. Considering India's populous cities, they range from having 500-800 public facilities
(https://pib.gov.in/PressReleasePage.aspx?PRID=1539877) and this doesn't even count the country as a whole that has over 20k hospitals.
![](Pasted%20image%2020230307130109.png)


#### Comparing IPFS to AWS S3

![](Pasted%20image%2020230307130614.png)
This chart displays a consistent pattern for storing data on IPFS over AWS, even with storage sizes increasing. The time required for actually storing on IPFS became less than 2.5ms even with 200kb of storage. From my viewpoint, this also does not take into consideration outside services and platforms that can reduce this time usage with an even larger set of data, such as Estuary on Filecoin.

#### Table 3 - Gas Costs
Looking at the gas cost to verify a proof on-chain in Table 3, they recognize that this method is feasible on Ethereum Mainnet but in reality, feasibility does not equate to what is optimal. 

Here we can see what the full gas costs will become, yet this is only considering Rinkeby's testnet and does not fully assume the state of Ethereum's blockchain when a program like this will be put into effect.
| **Smart Contract** | **Gas Cost**    |
| ------------------ | --------------- |
| Deploy verifier    | 1282112 GasUsed |
| VerifyTx           | 1896490 GasUsed |
| AddBeneficiary ISC | 1911490 GasUsed |

### Security Analysis

This section covers two theories around the protections that this program provides, with the first covering a bad actor gaining access to the EHRs in IPFS and the second considering if a beneficiary loses their E-card and it is obtained by a bad actor.

1. This explains that it is nearly impossible to decrypt all of the files because of 256 bit security. On top of this, the actor must first have access to the re-encryption key stored on the smart contract itself.
	1. The authors do not explain any further and I think they should have expounded upon different scenarios where gaining access to another part of the infrastructure might provide access to either the Cloud or the Stakeholders data.
2. This point relies on the beneficiary's pin/passphrase as the main barrier for a bad actor. This is detailed further by the government's involvement in the program as they would be able to disable accounts if a card has been stolen.
	1. This also covers new pins can be created, which I think is a lackluster argument as there might still be cases where individuals are manipulated to provide access to the system if there is only a passphrase protecting them.

### Conclusion