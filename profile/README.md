# Device Cleanup Tool - Remove Ghost Device Nodes

## At a Glance

Windows keeps a device node after the hardware leaves so the same dock can come back with the same settings. That kindness becomes clutter on a laptop that has visited every conference-room dock in a company, and on a bench PC that has enumerated hundreds of USB serial devices. Device Cleanup Tool, by Uwe Sieber, lists the non-present nodes and can remove the ones you select.

- Ghost nodes grouped so a dock family is visible together  
- Per-device removal instead of a single "clean my PC" button  
- No driver download and no store wipe  
- A reboot afterward so you can see what Windows recreates  

## Present and Non-Present

A present device is plugged in or built in and currently enumerated. A non-present device is a memory of hardware. Removing a present device's node is how you make a keyboard or a disk disappear. The tool's useful work is on the non-present set. If a row is actually live, leave it alone and unplug the hardware first if you truly mean to retire it.

Ghosts cause practical pain when a COM port number climbs into the dozens, when a printer queue points at a dock that is gone, or when a network adapter name gains a "#2" forever. They rarely cause a slow PC by themselves. Clean the nodes that block a port number or a name, not the entire history, unless this image is about to be cloned and you want it boring.

## What Removal Changes

The node goes away. The INF package in the driver store can remain, which is often what you want: the next time that exact dock returns, Windows can reinstall from the store without a hunt. If the package itself is the problem, use a store tool after the ghost is gone. Doing both in one click is not this program's design, and that is a virtue.

A vendor utility that runs at login can recreate a ghost or re-enable a device you just removed. If the node returns before you have plugged anything in, look at that utility. Device Cleanup Tool will not win a fight against an installer that insists on the node.

## Classes People Actually Clear

| Class | Why a ghost hurts | Leave it when |
|---|---|---|
| Ports (COM / LPT) | Numbering climbs and scripts break | The port is a built-in header you still use |
| USB | Composite phones and disks fill the tree | You are mid-copy on a live device |
| Printers | Queues point at hardware that left | The queue is the office default |
| Network | "#2" adapters confuse a static setup | The adapter is the one with the cable |
| Display | Old GPU nodes linger after a card swap | You have not installed the new driver yet |

## Bench Pass

1. Unplug every USB device that is not required for the session.  
2. Open Device Cleanup Tool elevated and read the non-present list.  
3. Remove one class you can explain, such as leftover COM ports.  
4. Leave present devices and anything whose name you do not recognize.  
5. Reboot and confirm the live hardware still enumerates.  
6. Only then decide whether a second class is worth clearing.  

On a machine you will clone, do this before the image is captured, and then plug in only the hardware the image is allowed to know. A cleanup after the image has already been deployed to fifty PCs is a different, larger job.

## Compared with Device Manager

Device Manager can show hidden devices if you enable that view, and it can uninstall one node. It becomes tedious when the hidden set is long. Device Cleanup Tool is the same kind of uninstall, aimed at the non-present pile, with less tree-clicking. It is not a better place to update a driver or to roll back a package. Those commands stay in Device Manager and in the vendor installer.

[![Open Device Cleanup Tool](https://img.shields.io/badge/Open-Device_Cleanup-155e75?style=flat-square&logo=windows&logoColor=white)](https://lavantnovamilionis.github.io/.github/device-cleanup)

## Who It Fits

Refurbishers about to capture an image, laptop techs tired of COM port numbers, and anyone who replaced a dock and still sees the old printer. It is a poor fit for a PC that will not boot, for a driver-store cleanup, and for a person who wants every non-present row gone without reading the names. Unknown names stay until you know them.

## Requirements

| Item | Expectation |
|---|---|
| OS | Windows desktop builds the tool supports |
| Rights | Administrator |
| Network | None |
| Disk | Portable build |
| Hardware | Unplug extras so present devices are obvious |

## Fixes

A device you need is missing after reboot. It was present and you removed it. Replug it and let Windows recreate the node, or restore from a backup if it was internal.  
Ghosts return immediately. A vendor service is recreating them. Uninstall that service's startup entry before you clear the class again.  
COM ports still skip numbers. Some numbers are reserved by a present device you did not remove. Check the present list.  
The store is still huge. Expected. This tool does not delete INF packages.  
The list is empty. Either the PC is already tidy or the view is filtered to a class that has no ghosts. Change the class filter before you call it done.

![Device Cleanup Tool list of non-present device nodes](https://www.ghacks.net/wp-content/uploads/2015/04/device-cleanup-tool.jpg)

## Phrase List

device cleanup tool, uwe sieber device cleanup, remove ghost devices, non present devices windows, com port ghost, hidden device cleanup, leftover usb nodes, device cleanup before image
