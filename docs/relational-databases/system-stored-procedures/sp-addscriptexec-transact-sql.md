---
description: sp_addscriptexec (Transact-SQL)
title: sp_addscriptexec (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addscriptexec
- sp_addscriptexec_TSQL
helpviewer_keywords:
- sp_addscriptexec
ms.assetid: 1627db41-6a80-45b6-b0b9-c0b7f9a1c886
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 81d3b8ac9e8eda12ed27099fed5623d0fd3da489
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89536769"
---
# <a name="sp_addscriptexec-transact-sql"></a>sp_addscriptexec (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отсылает SQL-скрипт (SQL-файл) всем подписчикам публикации. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addscriptexec [ @publication = ] publication  
    [ , [ @scriptfile = ] 'scriptfile' ]  
    [ , [ @skiperror = ] 'skiperror' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @scriptfile = ] 'scriptfile'` Полный путь к файлу скрипта SQL. *scriptfile* имеет тип **nvarchar (4000)** и не имеет значения по умолчанию.  
  
`[ @skiperror = ] 'skiperror'` Указывает, должна ли агент распространения или агент слияния останавливаться при возникновении ошибки во время обработки скрипта. *SkipError* имеет **бит**и значение по умолчанию 0.  
  
 **0** = агент будет останавливаться.  
  
 **1** = агент продолжит выполнение скрипта и игнорирует ошибку.  
  
`[ @publisher = ] 'publisher'` Указывает издателя, отличного от [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  При публикации с издателя не следует использовать *Издатель* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addscriptexec** используется в репликации транзакций и репликации слиянием.  
  
 **sp_addscriptexec** не используется для репликации моментальных снимков.  
  
 Чтобы использовать **sp_addscriptexec**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетная запись службы должна иметь разрешения на чтение и запись в расположении моментальных снимков и разрешения на чтение в расположении, где хранятся скрипты.  
  
 [Программа sqlcmd](../../tools/sqlcmd-utility.md) используется для выполнения скрипта на подписчике, а скрипт выполняется в контексте безопасности, который используется агент распространения или агент слияния при подключении к базе данных подписки. При запуске агента в предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вместо [sqlcmd](../../tools/sqlcmd-utility.md)используется [программа osql](../../tools/osql-utility.md) .  
  
 **sp_addscriptexec** полезен при применении скриптов для подписчиков и использует [sqlcmd](../../tools/sqlcmd-utility.md) для применения содержимого скрипта к подписчику. Однако, поскольку конфигурации подписчика могут различаться, скрипты, протестированные до отправки к издателю, могут по-прежнему вызывать ошибки у подписчика. *skiperror* предоставляет возможность агент распространения или агент слияния игнорировать ошибки и продолжать работу. Используйте [sqlcmd](../../tools/sqlcmd-utility.md) для тестирования скриптов перед выполнением **sp_addscriptexec**.  
  
> [!NOTE]  
>  Пропущенные ошибки по-прежнему будут фиксироваться в журнале агента для последующей справки.  
  
 Использование **sp_addscriptexec** для публикации файла скрипта для публикаций с использованием протокола FTP для доставки моментальных снимков поддерживается только для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_addscriptexec**.  
  
## <a name="see-also"></a>См. также  
 [Выполнение скриптов во время синхронизации &#40;программирование репликации на языке Transact-SQL&#41;](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)   
 [Синхронизация данных](../../relational-databases/replication/synchronize-data.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
