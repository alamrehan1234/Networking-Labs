# Lab 01 – Basic LAN Connectivity

## Objective
Build a small switched LAN and verify that two PCs in the same IPv4 subnet can communicate.

## Topology
![Basic LAN topology](topology.png)

## Devices and connections

| Device | Interface | Connected to |
|---|---|---|
| PC0 | FastEthernet0 | Switch Fa0/1 |
| PC1 | FastEthernet0 | Switch Fa0/2 |
| Switch | Cisco 2960 | Layer 2 access switch |

Use **Copper Straight-Through** cables for both connections.

## IP addressing

| Device | IPv4 address | Subnet mask | Default gateway |
|---|---|---|---|
| PC0 | 192.168.1.10 | 255.255.255.0 | Leave blank |
| PC1 | 192.168.1.20 | 255.255.255.0 | Leave blank |

Both PCs are in `192.168.1.0/24`, so they can communicate through the switch without a router or default gateway.

## Configuration steps

1. Add one Cisco 2960 switch and two PCs in Packet Tracer.
2. Connect PC0 to Fa0/1 and PC1 to Fa0/2.
3. Configure the IP addresses shown above using **Desktop → IP Configuration** on each PC.
4. Wait for the switch links to become active.
5. From PC0, open **Desktop → Command Prompt** and run:

```bash
ping 192.168.1.20
```

## Switch verification commands

```cisco
enable
show interfaces status
show mac address-table
show vlan brief
show running-config
```

The switch should learn the MAC addresses of the PCs after they exchange traffic (for example, after the ping).

## Expected result

- PC0 can successfully ping PC1.
- The switch ports connected to the PCs are up.
- The switch MAC address table learns the hosts' MAC addresses.

## Troubleshooting checklist

- Check both PC IP addresses and subnet masks.
- Confirm both cables are connected to the intended switch ports.
- Check that the switch ports are up.
- Confirm both PCs use the same subnet.
- Retry the ping after the first ARP exchange.

## Files in this folder

- `topology.png` – network diagram.
- `README.md` – lab objective, addressing, steps, verification and troubleshooting.
- `basic-connectivity.pkt` – create this file yourself in Cisco Packet Tracer using **File → Save As**. A valid Packet Tracer project must be saved by Packet Tracer; this sample pack does not fabricate a `.pkt` file.
