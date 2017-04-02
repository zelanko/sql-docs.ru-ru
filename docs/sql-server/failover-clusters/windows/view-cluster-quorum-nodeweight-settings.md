---
title: "Просмотр параметров NodeWeight кворума кластера | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "группы доступности [SQL Server], кластеры WSFC"
  - "кворум [SQL Server], AlwaysOn и кворум WSFC"
ms.assetid: b845e73a-bb01-4de2-aac2-8ac12abebc95
caps.latest.revision: 17
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 17
---
# Просмотр параметров NodeWeight кворума кластера
  В этом разделе описан порядок просмотра параметров NodeWeight для каждого узла элемента в кластере отказоустойчивого кластера Windows Server (WSFC). Параметры NodeWeight используются при определении голосов в кворуме для поддержки аварийного восстановления и сценариев с несколькими подсетями для экземпляров отказоустойчивого кластера [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   **Перед началом:**  [Предварительные требования](#Prerequisites), [Безопасность](#Security)  
  
-   **Просмотр параметров NodeWeight кворума с помощью:** [Использование Transact-SQL](#TsqlProcedure), [Использование Powershell](#PowerShellProcedure), [Использование Cluster.exe](#CommandPromptProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом работы  
  
###  <a name="Prerequisites"></a> Предварительные требования  
 Эта функция поддерживается только в [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] или более поздних версиях.  
  
> [!IMPORTANT]  
>  Для использования параметров NodeWeight необходимо применить следующее исправление ко всем серверам в кластере WSFC:  
>   
>  [KB2494036](http://support.microsoft.com/kb/2494036): доступно исправление, позволяющее настраивать узел кластера, не имеющий голосов кворума в [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] и в [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]  
  
> [!TIP]  
>  Если это исправление не установлено, то в примерах этого раздела будут возвращены пустые значения или значения NULL для NodeWeight.  
  
###  <a name="Security"></a> Безопасность  
 Пользователь должен входить в учетную запись домена, которая является членом локальной группы администраторов, на каждом узле кластера WSFC.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
##### Просмотр параметров NodeWeight  
  
1.  Подключитесь к любому экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в кластере.  
  
2.  Выполните запрос к представлению [sys].[dm_hadr_cluster_members].  
  
### Пример (Transact-SQL)  
 В следующем примере выполняется запрос к системному представлению для возврата значений для всех узлов в кластере данного экземпляра.  
  
```tsql  
SELECT  member_name, member_state_desc, number_of_quorum_votes  
 FROM   sys.dm_hadr_cluster_members;  
```  
  
##  <a name="PowerShellProcedure"></a> Использование Powershell  
  
##### Просмотр параметров NodeWeight  
  
1.  Запустите повышенный режим Windows PowerShell с помощью команды **Запуск от имени администратора**.  
  
2.  Импортируйте модуль `FailoverClusters` для включения командлетов кластера.  
  
3.  Использование объекта `Get-ClusterNode` для возврата коллекции объектов узла кластера.  
  
4.  Выведите свойства узла кластера в удобном для чтения формате.  
  
### Пример (Powershell)  
 В следующем примере показан вывод некоторых свойств узла для кластера с именем «Cluster001».  
  
```powershell  
Import-Module FailoverClusters  
  
$cluster = "Cluster001"  
$nodes = Get-ClusterNode -Cluster $cluster  
  
$nodes | Format-Table -property NodeName, State, NodeWeight  
```  
  
##  <a name="CommandPromptProcedure"></a> Использование Cluster.exe  
  
> [!NOTE]  
>  Программа cluster.exe является устаревшей в выпуске [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] .  Для будущих разработок используйте PowerShell с отказоустойчивым кластером.  Программа cluster.exe будет удалена в следующем выпуске Windows Server. Дополнительные сведения см. в разделе [Сопоставление команд Cluster.exe с командлетами Windows PowerShell для отказоустойчивых кластеров](http://technet.microsoft.com/library/ee619744\(WS.10\).aspx).  
  
##### Просмотр параметров NodeWeight  
  
1.  Запустите повышенный режим командной строки с помощью команды **Запуск от имени администратора**.  
  
2.  Использование **cluster.exe** для возврата состояния узла и значений NodeWeight  
  
### Пример (Cluster.exe)  
 В следующем примере показан вывод некоторых свойств узла для кластера с именем «Cluster001».  
  
```ms-dos  
cluster.exe Cluster001 node /status /properties  
```  
  
## См. также:  
 [Режим кворума и участвующая в голосовании конфигурация WSFC (SQL Server)](../../../sql-server/failover-clusters/windows/wsfc-quorum-modes-and-voting-configuration-sql-server.md)   
 [Настройка параметров NodeWeight кворума кластера](../../../sql-server/failover-clusters/windows/configure-cluster-quorum-nodeweight-settings.md)   
 [sys.dm_hadr_cluster_members (Transact-SQL)](../../../relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql.md)   
 [Командлеты отказоустойчивого кластера в Windows PowerShell по выполняемым задачам](http://technet.microsoft.com/library/ee619761\(WS.10\).aspx)  
  
  