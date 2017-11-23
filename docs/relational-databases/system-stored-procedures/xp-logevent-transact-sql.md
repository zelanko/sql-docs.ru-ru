---
title: "xp_logevent (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xp_logevent
- xp_logevent_TSQL
dev_langs: TSQL
helpviewer_keywords: xp_logevent
ms.assetid: 7b379ad0-5b12-4d2e-9c52-62465df1fdbd
caps.latest.revision: "30"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 27b644d0d804eeff22947f94cbb38ba9cc233adc
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="xplogevent-transact-sql"></a>xp_logevent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Заносит в журнал определенное пользователем сообщение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файла журнала и в средстве просмотра событий Windows. xp_logevent может использоваться для отправки предупреждения без посылки сообщения клиенту.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
xp_logevent { error_number , 'message' } [ , 'severity' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *ERROR_NUMBER*  
 Номер пользовательской ошибки, больший 50 000. Максимальное значение равно 2 147 483 647 (2^31 - 1).  
  
 **"** *сообщение* **"**  
 Символьная строка, которая может содержать не более 2048 символов.  
  
 **"** *серьезность* **"**  
 Является одним из трех символьных строк: ИНФОРМАЦИОННЫЕ, ПРЕДУПРЕЖДЕНИЯ или ошибки. *Серьезность* является необязательным, значение по умолчанию информационное сообщение.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Для приведенного примера кода процедура xp_logevent возвращает следующую строку ошибки:  
  
 `The command(s) completed successfully.`  
  
## <a name="remarks"></a>Замечания  
 При отправке сообщений от [!INCLUDE[tsql](../../includes/tsql-md.md)] процедур, триггеров, пакетов и т. д., использовать инструкцию RAISERROR вместо процедуры xp_logevent. xp_logevent не вызывает обработчик сообщений клиента и не задавайте@ERROR. Чтобы записывать сообщения в средство просмотра событий Windows и в файл журнала ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] внутри экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], следует выполнить инструкцию RAISERROR.  
  
## <a name="permissions"></a>Permissions  
 Необходимо членство в предопределенной роли базы данных db_owner в базе данных master или членство в предопределенной роли сервера sysadmin.  
  
## <a name="examples"></a>Примеры  
 Следующий пример записывает в журнал сообщение с переменными, переданными в сообщение, в средство просмотра событий Windows.  
  
```  
DECLARE @@TABNAME varchar(30, @@USERNAME varchar(30),DECLARE @@MESSAGE varchar(255);  
SET @@TABNAME = 'customers';  
SET @@USERNAME = USER_NAME();  
SELECT @@MESSAGE = 'The table ' + @@TABNAME + ' is not owned by the user   
   ' + @@USERNAME + '.';  
  
USE master;  
EXEC xp_logevent 60000, @@MESSAGE, informational;  
```  
  
## <a name="see-also"></a>См. также:  
 [PRINT (Transact-SQL)](../../t-sql/language-elements/print-transact-sql.md)   
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Общие расширенные хранимые процедуры &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)  
  
  
