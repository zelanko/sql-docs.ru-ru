---
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 00c5b4b94bc0a4347991944ccaa7898e75f244f0
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54130694"
---
# <a name="spaddscriptexec-transact-sql"></a>sp_addscriptexec (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [  **@publication=** ] **"**_публикации_**"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@scriptfile=** ] **"**_scriptfile_**"**  
 Полный путь к файлу скрипта SQL. *ScriptFile* — **nvarchar(4000)**, не имеет значения по умолчанию.  
  
 [  **@skiperror=** ] **"**_skiperror_**"**  
 Показывает, должен ли агент распространителя или агент слияния останавливаться при возникновении ошибки во время обработки скрипта. *SkipError* — **бит**, значение по умолчанию 0.  
  
 **0** = агент остановится.  
  
 **1** = агент пропустит ошибку и продолжит выполнение скрипта.  
  
 [  **@publisher=** ] **"**_издателя_**"**  
 Указывает, отличный от [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не должны использоваться при публикации из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addscriptexec** используется в транзакционной репликации и репликации слиянием.  
  
 **sp_addscriptexec** не используется для репликации моментальных снимков.  
  
 Чтобы использовать **sp_addscriptexec**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетная запись службы должна чтение и запись разрешения для разрешения расположения "и" чтение моментальных снимков в расположении, где сценарии хранятся.  
  
 [Служебная программа sqlcmd](../../tools/sqlcmd-utility.md) используется для выполнения сценария на подписчике, а сценарий выполняется в контексте безопасности, используемый агентом распространителя или агентом слияния при подключении к базе данных подписки. Когда агент выполняется на предыдущую версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [программа osql](../../tools/osql-utility.md) используется вместо [sqlcmd](../../tools/sqlcmd-utility.md).  
  
 **sp_addscriptexec** полезен применения скриптов к подписчикам и использует [sqlcmd](../../tools/sqlcmd-utility.md) для применения содержимое скрипта к подписчику. Однако, поскольку конфигурации подписчика могут различаться, скрипты, протестированные до отправки к издателю, могут по-прежнему вызывать ошибки у подписчика. *skiperror* предоставляет возможность агент распространителя или агенту слияния пропускать ошибки и продолжать работу. Используйте [sqlcmd](../../tools/sqlcmd-utility.md) Чтобы протестировать скрипты перед запуском **sp_addscriptexec**.  
  
> [!NOTE]  
>  Пропущенные ошибки по-прежнему будут фиксироваться в журнале агента для последующей справки.  
  
 С помощью **sp_addscriptexec** для файла скрипта для публикаций, использующих FTP для доставки моментальных снимков поддерживается только для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_addscriptexec**.  
  
## <a name="see-also"></a>См. также  
 [Выполнение скриптов во время синхронизации &#40;программирование репликации Transact-SQL&#41;](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)   
 [Синхронизация данных](../../relational-databases/replication/synchronize-data.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
