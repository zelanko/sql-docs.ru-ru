---
description: sp_who (Transact-SQL)
title: sp_who (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_who_TSQL
- sp_who
dev_langs:
- TSQL
helpviewer_keywords:
- sp_who
ms.assetid: 132dfb08-fa79-422e-97d4-b2c4579c6ac5
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a3d3af35b9d886e41d43e0c480c49a7e593e00f4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88463994"
---
# <a name="sp_who-transact-sql"></a>sp_who (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Предоставляет сведения о текущих пользователях, сеансах и процессах в экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] . Данные могут быть отфильтрованы, чтобы возвращать только те процессы, которые не простаивают, принадлежат конкретному пользователю или принадлежат определенному сеансу.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_who [ [ @loginame = ] 'login' | session ID | 'ACTIVE' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @loginame = ] 'login' | session ID | 'ACTIVE'` Используется для фильтрации результирующего набора.  
  
 Аргумент *Login* имеет тип **sysname** , определяющий процессы, принадлежащие конкретному имени входа.  
  
 *идентификатор сеанса* — это идентификационный номер сеанса, принадлежащий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляру. *идентификатор сеанса* — **smallint**.  
  
 **Active** исключает сеансы, ожидающие следующей команды от пользователя.  
  
 Если значение не указано, эта процедура возвращает все сеансы, принадлежащие экземпляру.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 **sp_who** возвращает результирующий набор со следующими сведениями.  
  
|Столбец|Тип данных|Описание|  
|------------|---------------|-----------------|  
|**spid**|**smallint**|Идентификатор сеанса.|  
|**ecid**|**smallint**|Идентификатор контекста выполнения заданного потока, связанный с определенным идентификатором сеанса.<br /><br /> ECID = {0, 1, 2, 3,... *n*}, где 0 всегда представляет главный или родительский поток, а {1, 2, 3,... *n*} представляет подпотоки.|  
|**status**|**nchar (30)**|Состояние процесса. Допустимые значения:<br /><br /> **неактивен**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сбрасывает сеанс.<br /><br /> **работает**. В сеансе выполняются один или несколько пакетов. Если включен режим MARS, в сеансе может выполняться несколько пакетов. Дополнительные сведения см. в статье [Использование множественных активных результирующих наборов &#40;MARS&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).<br /><br /> **фон**. В сеансе выполняется фоновая задача, например обнаружение взаимоблокировок.<br /><br /> **откат**. В сеансе выполняется откат транзакций.<br /><br /> **Ожидание**. В сеансе ожидается освобождение потока исполнителя.<br /><br /> **runnable**. Задачи сеанса находятся в очереди исполнителей планировщика, ожидая времени такта.<br /><br /> **spinloop**. Задачи сеанса ожидают освобождения взаимоблокировки.<br /><br /> **приостановлено**. Сеанс ожидает завершения события, например операции ввода-вывода.|  
|**loginame**|**nchar (128)**|Имя входа, связанное со специфическим процессом.|  
|**hostname**|**nchar (128)**|Имя узла или компьютера для каждого процесса.|  
|**blk**|**char (5)**|Идентификатор сеанса для блокирующего процесса, если такой существует. В противном случае значение этого столбца — 0.<br /><br /> Если транзакция, связанная с данным идентификатором сеанса, заблокирована потерянной распределенной транзакцией, этот столбец возвратит -2 для блокирующей потерянной транзакции.|  
|**dbname**|**nchar (128)**|База данных, используемая процессом.|  
|**cmd**|**nchar (16)**|Команда компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] (инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)], внутренний процесс компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и так далее), выполняющаяся для процесса. В SQL Server 2019 тип данных изменился на **nchar (26)**.|  
|**request_id**|**int**|Идентификатор для запросов, запущенных в определенном сеансе.|  
  
 При параллельной обработке подпроцессы создаются для определенного идентификатора сеанса. Главный поток обозначается как `spid = <xxx>` и `ecid =0`. Другие подпотоки совпадают `spid = <xxx>` , но с **ECID** > 0.  
  
## <a name="remarks"></a>Комментарии  
 Блокирующий процесс (который может иметь монопольную блокировку) является процессом, удерживающим ресурсы, в которых нуждается другой процесс.  
  
 Всем потерянным распределенным транзакциям назначается значение идентификатора сеанса, равное -2. Потерянные распределенные транзакции являются распределенными транзакциями, которые не связаны с каким-либо идентификатором сеанса. Дополнительные сведения см. в статье [Использование помеченных транзакций для согласованного восстановления связанных баз данных (модель полного восстановления)](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md).  
  
 Запросите столбец **is_user_process** sys. dm_exec_sessions, чтобы разделить системные процессы от пользовательских процессов.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение VIEW SERVER STATE на сервер для просмотра всех выполняющихся сеансов на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Иначе пользователь сможет увидеть только текущий сеанс.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-all-current-processes"></a>A. Перечень всех текущих процессов  
 В следующем примере используется хранимая процедура `sp_who` без параметров для возврата сведений обо всех текущих пользователях.  
  
```  
USE master;  
GO  
EXEC sp_who;  
GO  
```  
  
### <a name="b-listing-a-specific-users-process"></a>Б. Перечень процессов определенного пользователя  
 Следующий пример показывает, как просмотреть сведения об отдельном текущем пользователе по имени входа.  
  
```  
USE master;  
GO  
EXEC sp_who 'janetl';  
GO  
```  
  
### <a name="c-displaying-all-active-processes"></a>В. Отображение всех активных процессов  
  
```  
USE master;  
GO  
EXEC sp_who 'active';  
GO  
```  
  
### <a name="d-displaying-a-specific-process-identified-by-a-session-id"></a>Г. Отображение определенного процесса, определяемого идентификатором сеанса  
  
```  
USE master;  
GO  
EXEC sp_who '10' --specifies the process_id;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_lock (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md)   
 [sys.sysные процессы &#40;&#41;Transact-SQL ](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
