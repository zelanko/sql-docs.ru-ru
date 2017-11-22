---
title: "MSSQL_ENG014010 | Документация Майкрософт"
ms.custom: 
ms.date: 08/26/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSSQL_ENG014010 error
ms.assetid: 6ea84f2f-e7a2-4028-9ea9-af0d2eba660e
caps.latest.revision: "18"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 70dface53867d8f6f975b67a691ae754ed5fc3ff
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="mssqleng014010"></a>MSSQL_ENG014010
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14010|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Сервер "%s" не определен как сервер подписок.|  
  
## <a name="explanation"></a>Объяснение  
 Репликация предполагает, что все серверы в топологии должны быть зарегистрированы с использованием имени компьютера и необязательного имени экземпляра (в случае кластеризованного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имени виртуального сервера и необязательного имени экземпляра). Для правильного функционирования репликации необходимо, чтобы значение, возвращаемое `SELECT @@SERVERNAME` для каждого сервера в топологии, соответствовало имени компьютера или имени виртуального сервера с необязательным именем экземпляра.  
  
 Репликация не поддерживается, если какой-либо из экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] зарегистрирован при помощи IP-адреса или полностью определенного имени домена (FQDN). Данная ошибка может возникнуть, если при настройке репликации имеются какие-либо экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , зарегистрированные с помощью IP-адреса или FQDN в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
## <a name="user-action"></a>Действие пользователя  
 Убедитесь в том, что все экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в топологии должным образом зарегистрированы. Если сетевое имя компьютера отличается от имени экземпляра SQL Server.  
  
-   Добавьте уникальное имя данного экземпляра SQL Server в качестве допустимого сетевого имени. Один из методов установки альтернативного сетевого имени — это добавление имени в локальный файл hosts. Файл локальных узлов по умолчанию расположен в каталоге WINDOWS\system32\drivers\etc или WINNT\system32\drivers\etc. Дополнительные сведения см. в документации по Windows.  
  
     Например, если имя компьютера — comp1, IP-адрес компьютера — 10.193.17.129, имя экземпляра — inst1/instname, то следует добавить в файл hosts следующую запись:  
  
     10.193.17.129 inst1  
  
-   Удалите репликацию, зарегистрируйте каждый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а затем восстановите репликацию. Если значение @@SERVERNAME недопустимо для некластеризованного экземпляра, выполните следующие действия:  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     После выполнения хранимой процедуры [sp_addserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md) необходимо перезапустить службу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы изменения параметра @@SERVERNAME вступили в силу.  
  
     Если значение @@SERVERNAME недопустимо для кластеризованного экземпляра, необходимо изменить имя с помощью администратора кластера. Дополнительные сведения см. в разделе [Экземпляры отказоустойчивого кластера (режим AlwaysOn) (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).  
  
## <a name="see-also"></a>См. также:  
 [@@SERVERNAME &#40;Transact-SQL&#41;](../../t-sql/functions/servername-transact-sql.md)   
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
