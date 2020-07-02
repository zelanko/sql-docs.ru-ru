---
title: xp_logevent (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_logevent
- xp_logevent_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_logevent
ms.assetid: 7b379ad0-5b12-4d2e-9c52-62465df1fdbd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b19aa23d0009900045d5298c095f6c5a4347d633
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85755567"
---
# <a name="xp_logevent-transact-sql"></a>xp_logevent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Записывает определяемое пользователем сообщение в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файл журнала и в Просмотр событий Windows. xp_logevent можно использовать для отправки предупреждения без отправки клиенту сообщения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
xp_logevent { error_number , 'message' } [ , 'severity' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *error_number*  
 Номер пользовательской ошибки, больший 50 000. Максимальное значение равно 2 147 483 647 (2^31 - 1).  
  
 **"** *сообщение* **"**  
 Символьная строка, которая может содержать не более 2048 символов.  
  
 **"** *серьезность* **"**  
 — Одна из трех символьных строк: ИНФОРМАЦИОНное, предупреждение или ошибка. *уровень серьезности* является необязательным и имеет по умолчанию информационный.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Для приведенного примера кода процедура xp_logevent возвращает следующую строку ошибки:  
  
 `The command(s) completed successfully.`  
  
## <a name="remarks"></a>Примечания  
 При отправке сообщений из [!INCLUDE[tsql](../../includes/tsql-md.md)] процедур, триггеров, пакетов и т. д. Используйте инструкцию RAISERROR вместо xp_logevent. xp_logevent не вызывает обработчик сообщений клиента или Set @ @ERROR . Чтобы записывать сообщения в средство просмотра событий Windows и в файл журнала ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] внутри экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], следует выполнить инструкцию RAISERROR.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли базы данных db_owner в базе данных master или членство в предопределенной роли сервера sysadmin.  
  
## <a name="examples"></a>Примеры  
 Следующий пример записывает в журнал сообщение с переменными, переданными в сообщение, в средство просмотра событий Windows.  
  
```  
DECLARE @@TABNAME varchar(30), @@USERNAME varchar(30), @@MESSAGE varchar(255);  
SET @@TABNAME = 'customers';  
SET @@USERNAME = USER_NAME();  
SELECT @@MESSAGE = 'The table ' + @@TABNAME + ' is not owned by the user   
   ' + @@USERNAME + '.';  
  
USE master;  
EXEC xp_logevent 60000, @@MESSAGE, informational;  
```  
  
## <a name="see-also"></a>См. также  
 [PRINT (Transact-SQL)](../../t-sql/language-elements/print-transact-sql.md)   
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Общие расширенные хранимые процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)  
  
  
