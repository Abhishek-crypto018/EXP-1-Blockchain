### Experiment 1: Decentralized Certificate Verification
## Aim:
  To develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity.
## Algorithm:
1. Deploy a smart contract where universities can issue certificates.
2. Store a hash of certificate data on-chain.
3. Provide a verification function that checks certificate authenticity.
4. Users can verify the certificate by comparing the stored hash.
## Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;
contract CertificateVerification {
address public university;
mapping(bytes32 => bool) public certificates; // Store hashed certificates
event CertificateIssued(bytes32 indexed certHash);
constructor() {
university = msg.sender; // University deploys the contract
}
function issueCertificate(string memory studentName, string memory degree, uint256 year) public {
require(msg.sender == university, "Only university can issue certificates");
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
certificates[certHash] = true;
emit CertificateIssued(certHash);
}
function verifyCertificate(string memory studentName, string memory degree, uint256 year) public view returns (bool) {
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
return certificates[certHash];
}
}
```
# Expected Output:
```
● When the university issues a certificate, it gets stored as a hash.
● A student or employer can verify the certificate by entering the details.
● If valid, it returns true; otherwise, false.
High-Level Overview:
● Used to prevent fake certificates.
● Enables quick verification by employers or other institutions.
● Shows how blockchain can be used in education and credential verification.
```

<img width="1920" height="1080" alt="Screenshot 2026-11-06 160159" src="https://github.com/user-attachments/assets/cc7f3f26-70f5-419e-965f-df0ee26e71d6" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/414b3678-f048-4065-89d1-a48264103c3b" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4c59c683-9775-46ee-9f9b-0b2aa8151d32" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/baf629e5-6fea-499f-85c4-a5769d3e7ac8" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f3fc4ec5-22cd-42d8-9c1b-b6ab674b25c0" />




# Result:
Thus, the experiment to develop a smart contract for issuing and verifying academic certificates on Ethereum has been completed successfully and the output is verified.
