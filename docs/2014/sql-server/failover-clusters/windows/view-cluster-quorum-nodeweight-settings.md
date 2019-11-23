---
title: Просмотр параметров NodeWeight кворума кластера | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
ms.assetid: b845e73a-bb01-4de2-aac2-8ac12abebc95
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 12d68b8494fee4400c0a8e9ec043f0972ba2de5c
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72783355"
---
# <a name="view-cluster-quorum-nodeweight-settings"></a>Просмотр параметров NodeWeight кворума кластера
  В этом разделе описан порядок просмотра параметров NodeWeight для каждого узла элемента в кластере отказоустойчивого кластера Windows Server (WSFC). Параметры NodeWeight используются при определении голосов в кворуме для поддержки аварийного восстановления и сценариев с несколькими подсетями для экземпляров отказоустойчивого кластера [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   **Перед началом:**  [Предварительные требования](#Prerequisites), [Безопасность](#Security)  
  
-   **Просмотр параметров NodeWeight кворума с помощью:** [Использование Transact-SQL](#TsqlProcedure), [Использование Powershell](#PowerShellProcedure), [Использование Cluster.exe](#CommandPromptProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом работы  
  
###  <a name="Prerequisites"></a> Предварительные требования  
 Эта функция поддерживается только в [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] или более поздних версиях.  
  
> [!IMPORTANT]  
>  Для использования параметров NodeWeight необходимо применить следующее исправление ко всем серверам в кластере WSFC:  
>   
>  [KB2494036](https://support.microsoft.com/kb/2494036): доступно исправление, позволяющее настраивать узел кластера, не имеющий голосов кворума в [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] и в [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]  
  
> [!TIP]  
>  Если это исправление не установлено, то в примерах этого раздела будут возвращены пустые значения или значения NULL для NodeWeight.  
  
###  <a name="Security"></a> Безопасность  
 Пользователь должен входить в учетную запись домена, которая является членом локальной группы администраторов, на каждом узле кластера WSFC.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
##### <a name="to-view-nodeweight-settings"></a>Просмотр параметров NodeWeight  
  
1.  Подключитесь к любому экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в кластере.  
  
2.  Выполните запрос к представлению [sys].[dm_hadr_cluster_members].  
  
### <a name="example-transact-sql"></a>Пример (Transact-SQL)  
 В следующем примере выполняется запрос к системному представлению для возврата значений для всех узлов в кластере данного экземпляра.  
  
```sql  
SELECT  member_name, member_state_desc, number_of_quorum_votes  
 FROM   sys.dm_hadr_cluster_members;  
```  
  
##  <a name="PowerShellProcedure"></a> Использование Powershell  
  
### <a name="to-view-nodeweight-settings"></a>Просмотр параметров NodeWeight
  
1.  Запустите повышенный режим Windows PowerShell с помощью команды **Запуск от имени администратора**.  
  
2.  Импортируйте модуль `FailoverClusters` для включения командлетов кластера.  
  
3.  Использование объекта `Get-ClusterNode` для возврата коллекции объектов узла кластера.  
  
4.  Выведите свойства узла кластера в удобном для чтения формате.  
  
### <a name="example-powershell"></a>Пример (Powershell)  
 В следующем примере показан вывод некоторых свойств узла для кластера с именем Cluster001.  
  
```powershell  
Import-Module FailoverClusters  
  
$cluster = "Cluster001"  
$nodes = Get-ClusterNode -Cluster $cluster  
  
$nodes | Format-Table -Property NodeName, State, NodeWeight  
```  
  
##  <a name="CommandPromptProcedure"></a> Использование Cluster.exe  
  
> [!NOTE]  
>  Программа cluster.exe является устаревшей в выпуске [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] .  Для будущих разработок используйте PowerShell с отказоустойчивым кластером.  Программа cluster.exe будет удалена в следующем выпуске Windows Server. Дополнительные сведения см. в разделе [Сопоставление команд Cluster.exe с командлетами Windows PowerShell для отказоустойчивых кластеров](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx).  
  
##### <a name="to-view-nodeweight-settings"></a>Просмотр параметров NodeWeight  
  
1.  Запустите повышенный режим командной строки с помощью команды **Запуск от имени администратора**.  
  
2.  Использование **cluster.exe** для возврата состояния узла и значений NodeWeight  
  
### <a name="example-clusterexe"></a>Пример (Cluster.exe)  
 В следующем примере показан вывод некоторых свойств узла для кластера с именем Cluster001.  
  
```cmd
cluster.exe Cluster001 node /status /properties  
```  
  
## <a name="see-also"></a>См. также статью  
 [Режим кворума и участвующая в голосовании конфигурация WSFC (SQL Server)](wsfc-quorum-modes-and-voting-configuration-sql-server.md)   
 [Настройка параметров NodeWeight кворума кластера](configure-cluster-quorum-nodeweight-settings.md)   
 [sys.dm_hadr_cluster_members (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)   
 [Командлеты отказоустойчивого кластера в Windows PowerShell по выполняемым задачам](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)  
