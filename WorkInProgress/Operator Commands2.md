[Adabas Review 5.1.1](https://documentation.softwareag.com/adabas/rev511/overview.htm) [Installation and Operations for BS2000](https://documentation.softwareag.com/adabas/rev511/inst_bs2/bs2over.htm) Operator Commands

[ ](https://documentation.softwareag.com/adabas/rev511/inst_bs2/opcoms.htm#)

# Operator Commands

The commands in this section of the documentation are used to control the Adabas Review (ADAREV).

The operator commands perform the following general types of operations:

- Terminate an Adabas or user session;
- Display nucleus or utility information;
- Log commands into CLOG;
- Change Adabas operating parameters or conditions.

The commands are listed alphabetically.

This document covers the following topics:

- [Entering Operator Commands](https://documentation.softwareag.com/adabas/rev511/inst_bs2/opcoms.htm#d0e162)
- [Operator Command Overview](https://documentation.softwareag.com/adabas/rev511/inst_bs2/opcoms.htm#opcmdov)

------

## Entering Operator Commands

The ADAREV operator commands are entered the same way as other Adabas operator commands.

In BS2000 environments, enter each command at the operator console by addressing the Adabas nucleus with its task sequence number (TSN) in the following form:

```
/INTR  TSN,command
```

For testing purposes, the nucleus may be run as a dialog process. The nucleus may be interrupted by pressing the K2 key, after which the prompt "/" appears. Now an operator command can be sent to the nucleus in the following form:

```
/INTR  command
```

**Note:**
In the dialog mode, the nucleus stops as long as the INTR message is not sent back. The resume statement /RESUME causes the nucleus to resume where it was interrupted when no operator command is issued.

Operator commands are processed by a STXIT routine.

## Operator Command Overview

The remainder of the section describes the commands that an Adabas Review operator can enter from the console.

- [ADAEND Operator Command](https://documentation.softwareag.com/adabas/rev511/inst_bs2/opcoms.htm#ADAEND)
- [CANCEL Operator Command](https://documentation.softwareag.com/adabas/rev511/inst_bs2/opcoms.htm#CANCEL)
- [DCLIENT Operator Command](https://documentation.softwareag.com/adabas/rev511/inst_bs2/opcoms.htm#DCLIENT)
- [DCQ Operator Command](https://documentation.softwareag.com/adabas/rev511/inst_bs2/opcoms.htm#DCQ)
- [DNC Operator Command](https://documentation.softwareag.com/adabas/rev511/inst_bs2/opcoms.htm#DNC)
- [STARTCLIENT Operator Command](https://documentation.softwareag.com/adabas/rev511/inst_bs2/opcoms.htm#STARTCLIENT)
- [STOPCLIENT Operator Command](https://documentation.softwareag.com/adabas/rev511/inst_bs2/opcoms.htm#STOPCLIENT)
- [Adabas Operator Commands](https://documentation.softwareag.com/adabas/rev511/inst_bs2/opcoms.htm#adaopcmds)

### ADAEND Operator Command

Use the ADAEND operator command to terminate an ADAREV session normally; the Adabas Review nucleus is terminated normally. No new monitoring commands are accepted and all currently queued requests are dropped.

### CANCEL Operator Command

Use the CANCEL operator command to terminate ADAREV immediately; the Adabas Review nucleus is abnormally terminated and the job aborts with a user completion code of 253.

### DCLIENT Operator Command

![graphics/review_dclient.png](https://documentation.softwareag.com/adabas/rev511/inst_bs2/graphics/review_dclient.png)

Use the DCLIENT operator command to display information about the specified client or about all (ALL) clients. DCLIENT displays the number of clients currently registered with the hub and the individual status of each client, including the client's DBID, the associated nucleus IDs (for cluster databases), the time of last activity, the number of DBID=ALL reports, the number of database reports, any buffers required by the client, and the total number of monitoring data records received from the client. The following is an example of the message output:

```
REVH13 11135 Dbid Nucid Last-act Rpts Buffers Log-records
REVH13 11135 00001       22:15:18 01/01 FRSVIM 2222
REVH13 11135 00002       --:--:-- 01/00 ------ 0
REVH13 11135 00129       --:--:-- 01/02 -R---- 0
REVH13 11135 00129-00120 22:15:18 00/00 ------ 1
REVH13 11135 00129-00177 22:15:20 00/00 ------ 170
REVH13 11135 00129-00230 --:--:-- 00/00 ------ 0
```

In this example:

- Database 001 has one DBID=ALL report and one database-specific report running (01/01) and six specific buffers requested: the format buffer (F), the record buffer (R), the search buffer (S), the value buffer (V), the ISN buffer (I), and the multifetch buffer (M). This database sent 2222 log records to the hub.
- Database 002 has only one DBID=ALL report running (01/00) and no specific buffers are requested. This database has not yet sent any log records to the hub.
- Finally, database 129 is a cluster database with three nucleus IDs (00120, 00177, and 00230). It has one DBID=ALL report running and two database-specific reports (01/02). A record buffer only is requested. This report and buffer information is not repeated for each nucleus in the cluster, but the individual values for last activity time and the number of log records submitted to the hub for each nucleus is shown.

### DCQ Operator Command

Use the DCQ command to display the entire list of queued requests. The DCQ displays the sequence number, client's job name, client's user ID, request code, and status flags for each queued request.

**Note:**
If a large value was set for NC (as is recommended), the DCQ request may incur delays in the Adabas Review hub processing if a large number of queue elements must be displayed. Also, the display on the operator console may fill the console's buffers causing further system delays.

The following is an example of the message output:

```
AREV07 hubid  0000000013 NEXT EXPECTED SEQUENCE NUMBER
AREV07 hubid  0000000011 ADASMP    ARVU D   (C1D9E5E400C40000)  PC 2800
AREV07 hubid  0000000012 ADASMP    ARVU D   (C1D9E5E400C40000)  PC 2800  
```

### DNC Operator Command

Use the DNC operator command to display the number of queued requests currently in the command queue.

### STARTCLIENT Operator Command

![graphics/review_startclient.png](https://documentation.softwareag.com/adabas/rev511/inst_bs2/graphics/review_startclient.png)

Use the STARTCLIENT operator command to initiate a change order command to the specified client or to all (ALL) clients informing them to begin sending monitoring data to the hub. The change order is only sent to registered clients (clients that appear on the DCLIENT operator command display).

**Note:**
A change order changes a client's operation only if the monitoring status has been changed. This occurs only in cases where a previous STOPCLIENT operator command had been issued.

### STOPCLIENT Operator Command

![graphics/review_stopclient.png](https://documentation.softwareag.com/adabas/rev511/inst_bs2/graphics/review_stopclient.png)

Use the STOPCLIENT operator command to initiate a change order command to the specified client or to all (ALL) clients informing them to stop sending monitoring data. The change order is only sent to registered clients (clients that appear on the DCLIENT operator command display).

### Adabas Operator Commands

The following operator commands can be entered to monitor and control Adabas nucleus operation.

- [ADAEND](https://documentation.softwareag.com/adabas/rev511/inst_bs2/opcoms.htm#ada_ADAEND)
- [CANCEL](https://documentation.softwareag.com/adabas/rev511/inst_bs2/opcoms.htm#ada_CANCEL)

#### ADAEND

Terminates the Adabas session normally. No new users are accepted after this command has been issued. ET logic updating continues until the end of the current logical transaction for each user. After all activity has been completed as described above, the Adabas session is terminated.

#### CANCEL

Terminates the Adabas session immediately. All command processing is immediately suspended. A pending AUTORESTART is in effect, which in turn causes the AUTORESTART routine to be executed during the initialization of the next Adabas session.