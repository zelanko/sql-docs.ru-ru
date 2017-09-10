---
title: "Завершение работы (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SHUTDOWN_TSQL
- SHUTDOWN
dev_langs:
- TSQL
helpviewer_keywords:
- SQL Server, stopping
- shutting down SQL Server
- SHUTDOWN statement
- stopping SQL Server
- immediately stopping SQL Server
ms.assetid: c8b03ff9-688c-4fe8-86e8-bd6bd401c9a4
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a959b807bf566eab860b93350ebe07664e4965fa
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="shutdown-transact-sql"></a>SHUTDOWN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Немедленно останавливает SQL Server.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SHUTDOWN [ WITH NOWAIT ]   
```  
  
## <a name="arguments"></a>Аргументы  
 WITH NOWAIT  
 Необязательно. Закрывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], не выполнив контрольные точки в каждой базе данных. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] осуществляет выход после попытки завершить все пользовательские процессы. При перезапуске сервера ко всем незавершенным транзакциям применяется откат.  
  
## <a name="remarks"></a>Замечания  
 Если не используется параметр WITHNOWAIT, Shutdown закрывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по:  
  
1.  Отключает имена входа (за исключением членов **sysadmin** и **serveradmin** предопределенных ролей сервера).  
  
    > [!NOTE]  
    >  Для вывода списка всех текущих пользователей запустите **sp_who**.  
  
2.  Ожидает завершения выполняющихся инструкций Transact-SQL и хранимых процедур. Для вывода списка всех активных процессов и блокировок запустите **sp_who** и **sp_lock**соответственно.  
  
3.  Вставляет контрольную точку в каждую базу данных.  
  
 Использование инструкции SHUTDOWN сводит к минимуму автоматического восстановления работы необходимой при члены **sysadmin** фиксированной роли перезапуск сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Для остановки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно использовать другие инструменты и методы. Каждый из них выполняет контрольные точки во всех базах данных. Можно сбросить зафиксированные данные из кэша данных и остановить сервер:  
  
-   с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];  
  
-   Запустив **mssqlserver net stop** из командной строки для экземпляра по умолчанию или запустив **net stop mssql$***instancename* из командной строки для именованного экземпляра.  
  
-   с помощью служб на панели управления.  
  
 Если **sqlservr.exe** был запущен из командной строки, нажатие клавиш CTRL + C закрывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Однако при нажатии CTRL+C не вставляются контрольные точки.  
  
> [!NOTE]  
>  Использование любого из этих методов для остановки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отправляет сообщение `SERVICE_CONTROL_STOP` в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="permissions"></a>Permissions  
 Разрешения SHUTDOWN назначаются членам **sysadmin** и **serveradmin** предопределенных ролей сервера и они не могут передаваться.  
  
## <a name="see-also"></a>См. также:  
 [CHECKPOINT (Transact-SQL)](../../t-sql/language-elements/checkpoint-transact-sql.md)   
 [sp_lock &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md)   
 [sp_who &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)   
 [Приложение sqlservr](../../tools/sqlservr-application.md)   
 [Запуск, остановка, приостановка, возобновление и перезапуск компонента Database Engine, агента SQL и службы браузера SQL Server](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
