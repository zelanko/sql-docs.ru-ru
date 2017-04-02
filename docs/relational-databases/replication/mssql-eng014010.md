---
title: "MSSQL_ENG014010 | Microsoft Docs"
ms.custom: ""
ms.date: "08/26/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG014010, ошибка"
ms.assetid: 6ea84f2f-e7a2-4028-9ea9-af0d2eba660e
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# MSSQL_ENG014010
    
## Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14010|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Сервер "%s" не определен как сервер подписок.|  
  
## Объяснение  
 Репликация предполагает, что все серверы в топологии должны быть зарегистрированы с использованием имени компьютера и необязательного имени экземпляра (в случае кластеризованного экземпляра — имени виртуального сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и необязательного имени экземпляра). Для правильного функционирования репликации необходимо, чтобы значение, возвращаемое `SELECT @@SERVERNAME` для каждого сервера в топологии, соответствовало имени компьютера или имени виртуального сервера с необязательным именем экземпляра.  
  
 Репликация не поддерживается, если какой-либо из экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] зарегистрирован при помощи IP-адреса или полностью определенного имени домена (FQDN). Данная ошибка может возникнуть, если при настройке репликации имеются какие-либо экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , зарегистрированные с помощью IP-адреса или FQDN в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
## Действие пользователя  
 Убедитесь в том, что все экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в топологии должным образом зарегистрированы. Если сетевое имя компьютера отличается от имени экземпляра SQL Server.  
  
-   Добавьте уникальное имя данного экземпляра SQL Server в качестве допустимого сетевого имени. Один из методов установки альтернативного сетевого имени — это добавление имени в локальный файл hosts. Файл локальных узлов по умолчанию расположен в каталоге WINDOWS\system32\drivers\etc или WINNT\system32\drivers\etc. Дополнительные сведения см. в документации по Windows.  
  
     Например, если имя компьютера — comp1, IP-адрес компьютера — 10.193.17.129, имя экземпляра — inst1/instname, то следует добавить в файл hosts следующую запись:  
  
     10.193.17.129 inst1  
  
-   Удалите репликацию, зарегистрируйте каждый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а затем восстановите репликацию. Если значение @@SERVERNAME недопустимо для некластеризованного экземпляра, следуйте следующим инструкциям:  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     После выполнения хранимой процедуры [sp_addserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md) необходимо перезапустить службу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы изменения @@SERVERNAME вступили в силу.  
  
     Если значение @@SERVERNAME недопустимо для кластеризованного экземпляра, необходимо изменить имя с помощью приложения Cluster Administrator. Дополнительные сведения см. в разделе [Экземпляры отказоустойчивого кластера (режим AlwaysOn) (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).  
  
## См. также:  
 [@@SERVERNAME (Transact-SQL)](../../t-sql/functions/servername-transact-sql.md)   
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  