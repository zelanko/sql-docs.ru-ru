---
title: "MSSQL_ENG014117 | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014117 error
ms.assetid: e5906a76-9511-4c47-8826-8c765b58a39d
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b53e204550ce8f48b14e2b76667eb74fadc86346
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="mssqleng014117"></a>MSSQL_ENG014117
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14117|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|"%s" не настроена в качестве базы данных распространителя.|  
  
## <a name="explanation"></a>Объяснение  
 Эта ошибка может произойти, если истинны одно или оба из следующих условий:  
  
-   Отсутствует в **msdb..MSdistributiondbs**вход для указанной базы данных распространителя.  
  
-   Отсутствует или некорректен вход для локального сервера в базу данных **master** .  
  
     Репликация предполагает, что все серверы в топологии должны быть зарегистрированы с использованием имени компьютера и необязательного имени экземпляра (в случае кластеризованного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имени виртуального сервера и необязательного имени экземпляра). Для правильного функционирования репликации необходимо, чтобы значение, возвращаемое `SELECT @@SERVERNAME` для каждого сервера в топологии, соответствовало имени компьютера или имени виртуального сервера с необязательным именем экземпляра.  
  
     Репликация не поддерживается, если какой-либо из экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] зарегистрирован при помощи IP-адреса или полностью определенного имени домена (FQDN). Эта ошибка может возникать, если при настройке репликации любой из экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] был зарегистрирован по IP-адресу или по FQDN в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
## <a name="user-action"></a>Действие пользователя  
 Убедитесь, что экземпляр распространителя зарегистрирован правильно. Если сетевое имя компьютера отличается от имени экземпляра SQL Server.  
  
-   Добавьте уникальное имя данного экземпляра SQL Server в качестве допустимого сетевого имени. Один из методов установки альтернативного сетевого имени — это добавление имени в локальный файл hosts. Файл локальных узлов по умолчанию расположен в каталоге WINDOWS\system32\drivers\etc или WINNT\system32\drivers\etc. Дополнительные сведения см. в документации по Windows.  
  
     Например, если имя компьютера — comp1, IP-адрес компьютера — 10.193.17.129, имя экземпляра — inst1/instname, то следует добавить в файл hosts следующую запись:  
  
     10.193.17.129 inst1  
  
-   Отключите распространение, зарегистрируйте экземпляр и восстановите распространение. Если значение @@SERVERNAME недопустимо для некластеризованного экземпляра, выполните следующие действия:  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     После выполнения хранимой процедуры [sp_addserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md) необходимо перезапустить службу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы изменения параметра @@SERVERNAME вступили в силу.  
  
     Если значение @@SERVERNAME недопустимо для кластеризованного экземпляра, необходимо изменить имя с помощью администратора кластера. Дополнительные сведения см. в статье [Экземпляры отказоустойчивого кластера (режим AlwaysOn) (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).  
  
 После проверки верности регистрации экземпляра распространителя убедитесь в том, что база данных распространителя содержится в списке **msdb..MSdistributiondbs**. Если базы данных в списке нет:  
  
1.  Создайте скрипт конфигурации распространения. Дополнительные сведения см. в статье [Scripting Replication](../../relational-databases/replication/scripting-replication.md).  
  
2.  Отключите распространение, а затем включите его снова. Дополнительные сведения см. в статье [Настройка распространителя](../../relational-databases/replication/configure-distribution.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
