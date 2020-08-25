---
title: Запуск SQL Server в однопользовательском режиме | Документы Майкрософт
description: Сведения о однопользовательском режиме в SQL Server. Узнайте, когда это полезно, и как использовать параметр запуска -m для запуска экземпляра SQL Server в этом режиме.
ms.custom: ''
ms.date: 08/11/2020
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- starting SQL Server, single-user mode
- single-user mode [SQL Server]
ms.assetid: 72eb4fc1-7af4-4ec6-9e02-11a69e02748e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8651bcaa4aebf69eae9622031b49fb562b7be9f6
ms.sourcegitcommit: e4c36570c34cd7d7ae258061351bce6e54ea49f6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/12/2020
ms.locfileid: "88147305"
---
# <a name="start-sql-server-in-single-user-mode"></a>Запуск SQL Server в однопользовательском режиме
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  При определенных обстоятельствах экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] нужно запустить в однопользовательском режиме (используется **параметр запуска -m**). Например, может понадобиться изменить параметры конфигурации сервера, восстановить поврежденную базу данных master или другую системную базу данных. Для обоих этих действий необходим запуск экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в однопользовательском режиме.  
  
 После запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в однопользовательском режиме каждый член локальной группы администраторов на компьютере сможет подключаться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] от имени члена предопределенной роли сервера sysadmin. Дополнительные сведения см. в статье [Подключение к SQL Server в случае, если доступ системных администраторов заблокирован](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md).  
  
 При запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в однопользовательском режиме необходимо обратить внимание на следующее:  
  
-   Только один пользователь может подключиться к серверу.  
  
-   Процесс CHECKPOINT не выполняется. По умолчанию он автоматически выполняется при запуске.  
  
> [!NOTE]  
>  Перед подключением к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в однопользовательском режиме остановите службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В противном случае служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет использовать соединение, тем самым блокируя его  
  
Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запускается в однопользовательском режиме, среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] может подключаться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Обозреватель объектов в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] может вызвать ошибку, так как для некоторых операций ему необходимо одновременно несколько соединений. Чтобы управлять [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в однопользовательском режиме, выполняйте инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , подключаясь только через редактор запросов в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], или используйте [программу sqlcmd](../../tools/sqlcmd-utility.md).  
  
При использовании параметра **-m** с **SQLCMD** или [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] вы можете ограничить подключения к определенному клиентскому приложению. 

> [!NOTE]
> В Linux **SQLCMD** нужно указывать прописными буквами.

Например, **-m"SQLCMD"** разрешает только одно подключение, которое должно идентифицироваться как клиентская программа **SQLCMD**. Этот параметр следует использовать, когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запускается в однопользовательском режиме, а единственное доступное соединение занято неизвестным клиентским приложением. Чтобы подключиться с помощью редактора запросов в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], используйте **-m"Microsoft SQL Server Management Studio - Query"** .  
  
> [!IMPORTANT]  
>  Не используйте этот параметр как средство безопасности. Клиентское приложение предоставляет имя клиентского приложения и может указать ложное имя в составе строки подключения.  

Следующий пример запускает экземпляр SQL Server в однопользовательском режиме и разрешает подключение только через редактор запросов среды SQL Server Management Studio.

```console
net start "SQL Server (MSSQLSERVER)" -m"Microsoft SQL Server Management Studio - Query"
```

## <a name="note-for-clustered-installations"></a>Примечание для кластеризованной установки  
 Когда при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в кластерной среде выполняется запуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в однопользовательском режиме, DLL-библиотека ресурсов кластера использует доступное соединение, блокируя тем самым любые другие подключения к серверу. В таком состоянии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] попытка перевести ресурс агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режим «в сети», может привести к переходу ресурса SQL на другой узел, если этот ресурс настроен с учетом группы.  
  
 Для решения этой проблемы используется следующая процедура.  
  
1.  Удалите параметр запуска -m из дополнительных свойств [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Переведите ресурс [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режим «вне сети».  
  
3.  С текущего узла владельца этой группы выполните в командной строке следующую команду:  
    net start MSSQLSERVER /m.  
  
4.  Уточните у администратора кластера или с помощью консоли управления отказоустойчивым кластером, остается ли ресурс [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режиме «вне сети».  
  
5.  Подключитесь к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используя теперь следующую команду, и выполните необходимую операцию: SQLCMD -E -S\<servername>.  
  
6.  После завершения операции закройте командную строку и переведите SQL и другие ресурсы обратно в режим «в сети», обратившись к администратору кластера.  
  
## <a name="see-also"></a>См. также:  
 [Запуск, остановка или приостановка службы агента SQL Server](https://msdn.microsoft.com/library/c95a9759-dd30-4ab6-9ab0-087bb3bfb97c)   
 [Диагностическое соединение для администраторов баз данных](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)   
 [sqlcmd Utility](../../tools/sqlcmd-utility.md)   
 [CHECKPOINT (Transact-SQL)](../../t-sql/language-elements/checkpoint-transact-sql.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Параметры запуска службы Database Engine](../../database-engine/configure-windows/database-engine-service-startup-options.md)  
  
  
