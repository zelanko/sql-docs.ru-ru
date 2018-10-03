---
title: sp_dbcmptlevel (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbcmptlevel
- sp_dbcmptlevel_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbcmptlevel
ms.assetid: 508c686d-2bd4-41ba-8602-48ebca266659
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 094235cd508f4265a68861de60e9e4c2d35ee4b2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47841795"
---
# <a name="spdbcmptlevel-transact-sql"></a>sp_dbcmptlevel (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Настраивает определенное поведение баз данных для обеспечения совместимости с указанной версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте [уровень совместимости ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dbcmptlevel [ [ @dbname = ] name ]   
    [ , [ @new_cmptlevel = ] version ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@dbname=** ] *имя*  
 Имя базы данных, для которой должен быть изменен уровень совместимости. Имена баз данных должны соответствовать правилам для идентификаторов. *имя* — **sysname**, значение по умолчанию NULL.  
  
 [  **@new_cmptlevel=** ] *версии*  
 Версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с которой необходимо обеспечить совместимость базы данных. *версия* — **tinyint**, значение по умолчанию NULL. Это должно быть одно из следующих значений.  
  
 **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
 **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
 **110** = [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
 **120** = [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 **130** = [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если параметры не указаны или *имя* параметр не указан, **sp_dbcmptlevel** возвращает сообщение об ошибке.  
  
 Если *имя* указан без *версии*, [!INCLUDE[ssDE](../../includes/ssde-md.md)] возвращает сообщение, отображающее текущий уровень совместимости указанной базы данных.  
  
## <a name="remarks"></a>Примечания  
 Описание уровней совместимости, см. в разделе [уровень совместимости ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="permissions"></a>Разрешения  
 Только владелец базы данных, а члены **sysadmin** предопределенной роли сервера и **db_owner** предопределенной роли базы данных (при изменении текущей базы данных) могут выполнять эту процедуру.  
  
## <a name="see-also"></a>См. также  
 [Хранимым процедурам ядра СУБД &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [Зарезервированные ключевые слова (Transact-SQL)](../../t-sql/language-elements/reserved-keywords-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
