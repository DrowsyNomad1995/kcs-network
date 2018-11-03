# kcs-network
Asset Transaction Angular Application Proof of Concept(PoC)

to initiate the project clone it to your local system with Hyperledger VM 1.2

Please access  Hyperledger VM through the below link 

https://drive.google.com/file/d/16B6YTGl3e625HVBi3JTsBmuTUKoZgC61/view?usp=sharing


cd fabric-tools

./createPeerAdminCard.sh

./startFabric.sh 


cd kcs-network

composer archive create -t dir -n .

composer network install --card PeerAdmin@hlfv1 --archiveFile kcs-network@0.0.1.bna

composer network start --networkName kcs-network --networkVersion 0.0.1 --networkAdmin admin --networkAdminEnrollSecret adminpw --card PeerAdmin@hlfv1 --file networkadmin.card

composer card import --file networkadmin.card

composer network ping --card admin@tutorial-network

composer-rest-server -c admin@kcs-network -n never -w true


cd angular-app

npm start
