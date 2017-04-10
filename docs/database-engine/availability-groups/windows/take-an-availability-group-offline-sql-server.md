---
title: "Перевод группы доступности в режим &#171;вне сети&#187; (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "группы доступности [SQL Server], перевод в автономный режим"
ms.assetid: 50f5aad8-0dff-45ef-8350-f9596d3db898
caps.latest.revision: 38
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 37
---
# Перевод группы доступности в режим &#171;вне сети&#187; (SQL Server)
  В этом разделе описывается перевод группы доступности AlwaysOn из состояния ONLINE в состояние OFFLINE с помощью [!INCLUDE[tsql](../../../includes/tsql-md.md)] в [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] и более поздних версий. У баз данных с синхронной фиксацией потери данных не происходит, поскольку реплика с синхронной фиксацией не синхронизирована, режим OFFLINE вызывает ошибку, а группа доступности остается в режиме ONLINE. Продолжение работы группы доступности в режиме «в сети» защищает несинхронизированные базы данных с синхронной фиксацией от возможной потери данных. После перехода группы доступности в режим «вне сети» ее базы данных становятся недоступными для клиентов, при этом невозможно перевести группу доступности обратно в режим «в сети». Таким образом, переводить группу доступности в режим «вне сети» следует только в целях миграции ресурсов этой группы доступности с одного кластера WSFC на другой.  
  
 Если во время миграции [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] с одного кластера на другой какие-либо приложения подключаются напрямую к первичной реплике группы доступности, то эту группу доступности необходимо перевести в режим «вне сети». Миграция [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] поддерживает обновление операционной системы с минимальным временем простоя групп доступности. Типичный сценарий — использование миграции [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] с одного сервера на другой для обновления до [!INCLUDE[win8](../../../includes/win8-md.md)] или [!INCLUDE[win8srv](../../../includes/win8srv-md.md)]. Дополнительные сведения см. в документе [Миграция между кластерами групп доступности AlwaysOn для обновления ОС](http://msdn.microsoft.com/library/jj873730.aspx).  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Предварительные требования](#Prerequisites)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Перевод группы доступности в режим "вне сети" с использованием следующих средств:** [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.** [После перехода группы доступности в режим "вне сети"](#FollowUp)  
  
-   [См. также](#RelatedContent)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
> [!CAUTION]  
>  Используйте вариант OFFLINE только для миграции ресурсов группы доступности с одного кластера на другой.  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   На экземпляре сервера, где вводится команда OFFLINE, должны быть запущены службы [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] или более поздней версии (выпуск Enterprise Edition или более продвинутый выпуск).  
  
-   Группа доступности должна быть в данный момент в сети.  
  
###  <a name="Recommendations"></a> Рекомендации  
 Прежде чем переводить группу доступности в режим «вне сети», удалите прослушиватели группы доступности. Дополнительные сведения см. в статье [Удаление прослушивателя группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/remove-an-availability-group-listener-sql-server.md).  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Перевод группы доступности в режим «вне сети»**  
  
1.  Подключитесь к экземпляру сервера, где размещается реплика доступности для группы доступности. Эта реплика может быть первичной или вторичной.  
  
2.  Инструкция [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md) используется следующим образом:  
  
     ALTER AVAILABILITY GROUP *имя_группы* OFFLINE  
  
     где *имя_группы* — это имя группы доступности.  
  
### Пример  
 В следующем примере выполняется перевод группы доступности `AccountsAG` в режим «вне сети».  
  
```  
ALTER AVAILABILITY GROUP AccountsAG OFFLINE;  
```  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После перехода группы доступности в режим «вне сети»  
  
-   **Ведение журнала операций OFFLINE.**  Идентификатор узла WSFC, где была инициирована операция OFFLINE, сохраняется как в журнале кластера WSFC, так и в журнале SQL ERRORLOG.  
  
-   **Если прослушиватель группы доступности не был удален до перевода группы в режим "вне сети", выполните следующие действия.**  При переносе группы доступности на другой кластер WSFC удалите имя виртуальной сети и виртуальный IP-адрес прослушивателя. Их можно удалить с помощью консоли управления отказоустойчивым кластером либо с помощью командлета [Remove-ClusterResource](http://technet.microsoft.com/library/ee461015\(WS.10\).aspx) PowerShell или [cluster.exe](http://technet.microsoft.com/library/ee461015\(WS.10\).aspx). Обратите внимание, что программа cluster.exe в Windows 8 является устаревшей.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Удаление прослушивателя группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/remove-an-availability-group-listener-sql-server.md)  
  
-   [Смена контекста кластера HADR экземпляра сервера (SQL Server)](../../../database-engine/availability-groups/windows/change-the-hadr-cluster-context-of-server-instance-sql-server.md)  
  
##  <a name="RelatedContent"></a> См. также  
  
-   [Технические статьи по SQL Server 2012](http://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)  
  
-   [Блоги команды разработчиков SQL Server AlwaysOn: официальный блог по SQL Server AlwaysOn](http://blogs.msdn.com/b/sqlAlways%20On/)  
  
## См. также:  
 [Группы доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  