# SRv6 Docker-based Lab
It is just a simple docker-based SRv6 Lab

## Start the Lab
Run the `./lab_start.sh`
Then run `sh srv6_encaps_ipv4.sh`

## Access the Lab
Example command to access the R1: `docker exec -it R1 bash`

# if you want to steer IPv6 route, you may try below commands
`docker exec -it R1 ip -6 route add fc00:10:10:5::/64 encap seg6 mode encap segs fc00:10:10:10::20,fc00:10:10:30::40,fc00:10:10:50::50 dev eth1`

`docker exec -it R5 ip -6 route add fc00:10:10:1::/64 encap seg6 mode encap segs fc00:10:10:50::40,fc00:10:10:30::20,fc00:10:10:10::10 dev eth2`

# if you want to steer IPv4 route, you may try below commands
`docker exec -it R1 ip -4 route add 10.10.5.0/24 encap seg6 mode encap segs fc00:10:10:5:: dev eth0`

`docker exec -it R5 ip -4 route add 10.10.1.0/24 encap seg6 mode encap segs fc00:10:10:1:: dev eth0`

# if you would like to capture the traffic on a some segment you may refer to the below command, just change the example R1R2 example.
of course, you need to install tshark on your Linux.
` sudo tshark -i dm-`\`docker network ls | grep -i R1R2 | cut -d ' ' -f1\` -Y icmpv6 -V |grep -i source `

## Stop the Lab
Run the `./lab_stop.sh`

You can refer to example commands in the srv6_encaps_ipv4.sh
