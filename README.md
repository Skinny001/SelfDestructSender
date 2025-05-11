# SelfDestructSender
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

/**
 * @title SelfDestructSender
 * @dev A simple contract that self-destructs to send Ether to the EtherVault
 */
contract SelfDestructSender {
    // Address of the EtherVault contract
    address payable private vaultAddress;
    
    // Constructor - set the vault address when deploying
    constructor(address payable _vaultAddress) payable {
        vaultAddress = _vaultAddress;
        
         // Check if exactly 0.0005 ether was sent
        require(msg.value == 0.0005 ether, "Must send exactly 0.0005 ether");
        
        // Self-destruct and send the 0.0005 ether to the vault
        selfdestruct(vaultAddress);
    }
}


Wallet Information

Whitelisted Wallet Address: 0x372b4eB67006F68A9f296b23715055b8A878ABA9
Deployed Self-Destruct Contract: 0xda8122eeaa7ae01ce033ed152c59227fa1f7c6b1

# Project Overview
This repository contains my solution for the Great Ether Heist challenge. The goal was to interact with the EtherVault contract by sending Ether via a self-destruct contract and completing various challenges to increase withdrawal limits.

# Implementation
I've created a simple SelfDestructSender contract that:

Accepts exactly 0.0005 Ether when deployed
Self-destructs immediately after deployment, sending the Ether to the EtherVault contract
