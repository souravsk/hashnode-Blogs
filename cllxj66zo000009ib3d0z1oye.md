---
title: "Journalctl and system logging"
seoTitle: "What is journalctl ?"
datePublished: Wed Aug 30 2023 09:24:20 GMT+0000 (Coordinated Universal Time)
cuid: cllxj66zo000009ib3d0z1oye
slug: journalctl-and-system-logging
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693332866758/5a58635e-bb94-4201-aee1-009cef87ea97.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1693387349795/265ed033-8f61-4af6-8e70-4c714a026a09.png
tags: journal, linux, logging, systemd, journalctl

---

Hey Everyone in today's blog we will know what is journalctl and the use of this command.

# What is Journalctl?

**journald** is part of [systemd](https://systemd.io/) that deals with logging. **systemd**, at its core, is incharge of managing services: it starts them up and keeps them alive.

All services and systemd themselves need to log: “ssh started” or “user root logged in”, they might say. That’s where journald comes in: to capture these logs, record them, make them easy to find, and remove them when they pass a certain age.

`journalctl` is a command-line utility in Linux used to access and display logs from the systemd journal. The systemd journal is a centralized logging system that collects and manages log data generated by various components of the system, including the kernel, services, applications, and more.

# Journalctl features

Here are some key features and functionalities of `journalctl`:

1. **Unified Log Format:** The systemd journal stores log messages in a structured and binary format, providing more detailed information compared to traditional text-based log files.
    
2. **Timestamps and Metadata:** Each log entry in the journal includes a timestamp, hostname, priority level, and other metadata, making it easier to analyze and filter logs.
    
3. **Colorized Output:** By default, `journalctl` provides colorized output for different log levels, making it visually distinct and easier to read.
    
4. **Filtering and Querying:** You can use various options with `journalctl` to filter and query logs based on criteria such as time range, log level, unit (service) names, and more.
    
5. **Real-time Monitoring:** `journalctl` can be used to display logs in real-time as they are generated, similar to the `tail` command.
    
6. **Exporting and Forwarding Logs:** You can export log data from the journal or forward it to other systems for centralized log management and analysis.
    
7. **Persistent Storage:** The systemd journal stores logs persistently, even across reboots, unless configured otherwise. This can help in capturing historical log data for troubleshooting.
    
8. **Integration with Systemd:** `journalctl` is tightly integrated with systemd, the init system and service manager used in many Linux distributions. It allows you to explore logs related to various system units and services managed by systems.
    

# Basic Commands

Here are a few examples of how you can use `journalctl`:

* To display all logs:
    
    ```bash
    journalctl
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693050022041/17c341a0-2990-4e78-b8d0-f707827de422.png align="center")
    
* To display logs from a specific unit (service):
    
    ```bash
    journalctl -u nginx
    ```
    
* To display logs in real-time (follow mode):
    
    ```bash
    journalctl -f
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693055857419/654193d4-8665-4ef3-9ff4-f251baad633e.png align="center")
    
* To display logs from a specific time range:
    
    ```bash
    journalctl --since "2023-08-01" --until "2023-08-15"
    ```
    
* To display logs with a specific log level (e.g., errors and above):
    
    ```bash
    journalctl -p err
    ```
    
* To export logs to a file:
    
    ```bash
    journalctl > logs.txt
    ```
    

This is the way you can use journalctl to get the logs that will help you debug your problem.