---
title: "Configure Server Startup Options (SQL Server Configuration Manager) | Microsoft Docs"
ms.custom: ""
ms.date: "01/07/2016"
ms.prod: "sql-server-2014"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: conceptual
helpviewer_keywords: 
  - "parameters [SQL Server], startup options"
  - "SQL Server, startup options"
  - "single-user mode [SQL Server], starting in"
  - "startup options [SQL Server]"
  - "SQL Server services, setting startup options"
ms.assetid: 7a94643c-6460-4baf-bb31-0cb99eaf970d
caps.latest.revision: 31
author: "craigg-msft"
ms.author: "craigg"
manager: craigg
---
# Configure Server Startup Options (SQL Server Configuration Manager)
  This topic describes how to to configure startup options that will be used every time the [!INCLUDE[ssDE](../../includes/ssde-md.md)] starts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager. For a list of startup options, see [Database Engine Service Startup Options](database-engine-service-startup-options.md).  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
### Limitations and Restrictions  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager writes startup parameters to the registry. They take effect upon the next startup of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 On a cluster, changes must be made on the active server when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is online, and will take effect when the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is restarted. The registry update of the startup options on the other node will occur upon the next failover.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Configuring server startup options is restricted to users who can change the related entries in the registry. This includes the following users.  
  
-   Members of the local administrators group.  
  
-   The domain account that is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is configured to run under a domain account.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Configuration Manager  
  
#### To configure startup options  
  
1.  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, click **SQL Server Services**.  
  
    > [!NOTE]  
    >  Because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager is a snap-in for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console program and not a stand-alone program, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager does not appear as an application in newer versions of Windows.  
    >   
    >  -   **Windows 10**:  
    >          To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, on the **Start Page**, type SQLServerManager12.msc (for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]). For previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replace 12 with a smaller number. Clicking SQLServerManager12.msc opens the Configuration Manager. To pin the Configuration Manager to the Start Page or Task Bar, right-click SQLServerManager12.msc, and then click **Open file location**. In the Windows File Explorer, right-click SQLServerManager12.msc, and then click **Pin to Start** or **Pin to taskbar**.  
    > -   **Windows 8**:  
    >          To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager\<version>.msc** such as `SQLServerManager12.msc`, and then press **Enter**.  
  
2.  In the right pane, right-click **SQL Server (***<instance_name>***)**, and then click **Properties**.  
  
3.  On the **Startup Parameters** tab, in the **Specify a startup parameter** box, type the parameter, and then click **Add**.  
  
     For example, to start in single-user mode, type `-m` in the **Specify a startup parameter** box and then click **Add**. (When you restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode, stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent might connect first and prevent you from connecting as a second user.)  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  Restart the [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
    > [!WARNING]  
    >  After you are finished using single-user mode, in the Startup Parameters box, select the `-m` parameter in the **Existing Parameters** box, and then click **Remove**. Restart the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to restore [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to the typical multi-user mode.  
  
## See Also  
 [Start SQL Server in Single-User Mode](start-sql-server-in-single-user-mode.md)   
 [Connect to SQL Server When System Administrators Are Locked Out](connect-to-sql-server-when-system-administrators-are-locked-out.md)   
 [Start, Stop, or Pause the SQL Server Agent Service](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  