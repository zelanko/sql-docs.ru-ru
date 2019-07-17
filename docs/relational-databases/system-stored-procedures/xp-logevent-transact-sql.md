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
ms.openlocfilehash: 77275ee539a6367d7e2e04d03354155a5eff721d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68116643"
---
# <a name="xplogevent-transact-sql"></a>xp_logevent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Заносит в журнал определяемых пользователем сообщение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файл журнала и в средстве просмотра событий Windows. xp_logevent может использоваться для отправки предупреждения без посылки сообщения клиенту.  
  
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
 Является одним из трех символьных строк: ИНФОРМАЦИОННОЕ, предупреждение или ошибка. *уровень серьезности* является необязательным и по умолчанию — INFORMATIONAL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Для приведенного примера кода процедура xp_logevent возвращает следующую строку ошибки:  
  
 `The command(s) completed successfully.`  
  
## <a name="remarks"></a>Примечания  
 При отправке сообщений из [!INCLUDE[tsql](../../includes/tsql-md.md)] процедур, триггеров, пакетов и т. д., использовать инструкцию RAISERROR вместо процедуры xp_logevent. xp_logevent не вызывает обработчик сообщений клиента и не задает@ERROR. Чтобы записывать сообщения в средство просмотра событий Windows и в файл журнала ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] внутри экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], следует выполнить инструкцию RAISERROR.  
  
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
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Общие расширенные хранимые процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)  
  
  
