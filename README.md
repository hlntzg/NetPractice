# NetPractice

## Project overview

The project involves configuring small networks. As a general exercise, each network has issues that need to be fixed in order to ensure proper functionality. There are 10 levels to complete in order to finish the project. Examples of successfully completed levels can be found in the `my_config` directory.

### What is a Network?
A network in computing is a group of devices that can communicate with each other by sending and receiving data. The Internet is a prime example of a public network, connecting devices globally with minimal control. In contrast, private networks, such as home networks, restrict communication to specific devices, offering more security and control.

### What is TCP and IP address?
TCP (Transmission Control Protocol) is a protocol that ensures reliable data transfer across a network by breaking data into packets and reassembling them at the destination. It works with IP addresses, which are unique identifiers assigned to devices on a network. While TCP and IP are separate protocols, they work together to enable communication. This guide focuses on IPv4, the most widely used version of IP.

---

## NetPractice - Project

To succeed in the exercises, the unshaded fields must be updated until the network configuration is properly communicating. For each level, a non-functioning network diagram will be provided as an example, which I will use to explain my implementation of the exercises in the sections below.

<details>
  <summary>Level 1</summary>
  <br>

This level has a straightforward goal: ensure the devices that must direct communicate are in the same network. How to do it? Ensure the IP Addresses of each device are in the same range of possible IP addresses available for that network. Remember that the first and last IP are reserved for the Subnet Address and the Broadcast Address, so, anything else can be used if it is not yet assigned to a device.

For the Network A1-B1, the subnet mask is `255.255.255.0` (CIDR `/24`) which give us a total number of IP addresses of `256`. Host B has `104.97.23.12` as IP Address, therefore the Subnet Address is `104.97.23.0` and the Broadcast Address is `104.97.23.255`. That means that A1 can have any IP Address in this range (except the alreday taken). As the subnet mask is `/24`, only the last portion of the 32 bits IP would be different of each device inside that network.

In other case, C1-D1, the logic is similar, but because the subnet mask is `255.255.0.0` (CIDR `/16`), the only the first two octets (16 bits) of the IP Address would be the same in the IP Addresses of this network. To ensure that both hosts communicate between each other, their IP must be in the wide range (65.536) that this subnet mask allows - between `211.191.0.0` (Subnet Address) to `211.191.255.255` (Broadcast Address). Host C alreday has an IP Address (`211.191.223.75`), thus the Host D can have any IP from `211.191.0.1` to `211.191.255.254`.


  </details>

<details>
  <summary>Level 2</summary>
  <br>

All devices in the same network to have the same mask and, remember, it is only possible to use IP Address within the respective subnet mask range - the extremities IP Addresses are reserved for the Subnet Address and the Broadcast Address.

In the Network A1-B2, the subnet mask is defined by A1 as `255.255.255.224` (CIDR `/27`) and the IP Address of B1 is already set. These informations revele that the range of IP Address for network is 32, and since the first and last are reserved, the number of available IP Address is 30, and also, that this range should include `192.168.134.222` (IP Address of B1). So, the network range is between `192.168.36.192` and `192.168.36.223`, excluding the extremities (i.e., `192.168.36.192` and `192.168.36.223` are not part of the usable range). Therefore, host A can be assigned any IP address within this range.

Network C1-D1 has a narrow subnet mask set: `255.255.255.252` (CIDR `/30`) that allows only 4 IP Address in total (i.e., 2 IP Address available for hosts in the network. In this case, ensure to set the IP's in the correct range (and not reserved) and it is not a private address (how?).


  </details>

<details>
  <summary>Level 3</summary>
  <br>

The goal of this level is to allow communication between 3 devices: A1, B1, C1. All this hosts must be on the same network. One of these devices have alreday a subnet mask set (C1). Therefore, the mask `255.255.255.128` (CIDR `/25`) is the default for all the devices within the network, and it gives us information about the total range of IP Address: 128. So, we can assume that the range for this particular network is from `xxx.xxx.xxx.0` to `xxx.xxx.xxx.127` (excluding the extremities). The IP Address of one of the 3 host is already set: A1. This host IP is `104.198.50.125` which is within the range we just assume, and give us the network portion (24 bits) of the 32 bits IP Addresses for the others devices.

  </details>

<details>
  <summary>Level 4</summary>
  <br>

This network introduces a new element: a Router. This particular router has 3 interfaces with specifics IP Addresses and subnet masks, meaning it is possible to connect 3 networks to this device. The IP of the interface R1 must not overlap the ranges between other interfaces (R2, R3), and, of course, have to be within the available IP Address of the subnet mask of that network.

For the Network A1-B1-R1, the subnet mask should be choose based on the R2 and R3 mask's and IP Addresses. R2 mask is set to `255.255.255.128` (CIDR `/25`) and R3 mask is set to `255.255.255.192` (CIDR `/26`), so the range of IP Addresses of R2 is from `82.234.113.0` to `82.234.113.127` (CIDR /25 allows 128 IP's), while for R3 it is from `82.234.113.192` to `82.234.113.255` (CIDR /26 allows a range of 64 IP's). Within this informations, it is possible to set a appropriate subnet mask and IP Addresses for Network A1-B1-R1, ensuring that this particular network does not share any of those IP's from R2 and R3. 

R2:     Network portion is `82.234.113`, while the host portion range from `0` - `127`
R3:     Network portion is `82.234.113`, while the host portion range from `192` - `255`

The host portion of A1’s IP address is `132`, which lies exactly in between the host ranges of R2 and R3. The IP range from `82.234.113.128` to `82.234.113.191` provides exactly 64 available IP addresses. Therefore, a subnet mask of `255.255.255.192` (CIDR /`26`) or greater is appropriate. Ensure that the subnet mask chosen allows for at least 3 usable IP addresses (CIDR `/26` to `/29`). The next step is to assign the correct host portion of the IP address to R1 and B1 based on the chosen mask. Remember to exclude the extreme IP Addresses and avoid any overlapping IPs within router R’s subnet.

  </details>


<details>
  <summary>Level 5</summary>
  <br>

This level introduces the Router and the concept of Routing Table. Each host should have a routing table that allows the device to connect to the router and each other.

  </details>


<details>
  <summary>Level 6</summary>
  <br>

example of level 

  </details>


<details>
  <summary>Level 7</summary>
  <br>

example of level 

  </details>

<details>
  <summary>Level 8</summary>
  <br>

example of level 

  </details>

<details>
  <summary>Level 9</summary>
  <br>

example of level 

  </details>


<details>
  <summary>Level 10</summary>
  <br>

example of level 

  </details>

---

## General information

### Acknowledgments

- [NetworkChuck](https://youtu.be/5WfiTHiU4x8?si=nG4YrKvgIwYG8EY_) - Introductional playlist of subnetting. 

### Lessons learned from the project

- Basics of TCP/IP and how addressing works in a network.
- Understanding subnet mask (network and host portion), CIDR notation and IP Address range.
- Decimal to binary conversion! Concepts of octet and bits are truly important to this project!

### Permissions and disclaimer

Feel free to use and share this project. Please provide appropriate attribution when using or modifying it. This project is for educational purposes only. It may contain inaccurate information or terms.

### License

This project is licensed under a custom Educational Use License for Study Materials. Documentation, guidelines and study notes are licensed under [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/). See [LICENSE](./LICENSE) for full terms.

### Copyright and contact information

- Copyright (c) 2024 Helena Utzig.
- If you have any problems, questions, ideas or suggestions, please reach me out by helenautzig@gmail.com.
- Contact into the 42Network: https://profile.intra.42.fr/users/hutzig.
