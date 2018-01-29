        # create volume
        sudo docker volume create electroneum-blockchain
     
        # either run in foreground
        sudo docker run --name electroneumd -v electroneum-blockchain:/root/.electroneum -it r3lik/electroneum-full-node

        # or in background
        sudo docker run -d --name electroneumd -v electroneum-blockchain:/root/.electroneum -it r3lik/electroneum-full-node
