---
title: "По умолчанию DROP (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_DEFAULT_TSQL
- DROP DEFAULT
dev_langs:
- TSQL
helpviewer_keywords:
- DROP DEFAULT statement
- defaults [SQL Server], removing
ms.assetid: d2d3af25-8877-46ba-95d9-1844961d97ee
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cb7de5514d74ed4650d44bed145c32e9bea2c845
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drop-default-transact-sql"></a>DROP DEFAULT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет одно или несколько пользовательских значений по умолчанию из текущей базы данных.  
  
> [!IMPORTANT]  
>  DROP DEFAULT будут удалены в следующей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не используйте инструкции DROP DEFAULT в новых разработках и запланируйте модификацию приложений, использующих эту инструкцию в настоящее время. Вместо этого используйте определения по умолчанию, которые можно создавать с помощью ключевого слова DEFAULT [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) или [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DROP DEFAULT [ IF EXISTS ] { [ schema_name . ] default_name } [ ,...n ] [ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *ЕСЛИ СУЩЕСТВУЕТ*  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Условно удаляет значение по умолчанию только в том случае, если он уже существует.  
  
 *schema_name*  
 Имя схемы, которой принадлежит значение по умолчанию.  
  
 *default_name*  
 Имя существующего значения по умолчанию. Чтобы просмотреть список значений по умолчанию, которые существуют, выполните **sp_help**. Значения по умолчанию должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md). Задание имени схемы значения по умолчанию необязательно.  
  
## <a name="remarks"></a>Замечания  
 Перед удалением значение по умолчанию, привязку значения по умолчанию, выполнив **sp_unbindefault** Если значение по умолчанию привязано к столбцу или псевдониму типа данных.  
  
 После удаления значения по умолчанию из столбца, в котором допускаются значения NULL, везде на место значения вставляется NULL, если добавляются строки и явно не предоставляется никакое значение. После удаления значения по умолчанию из столбца со свойством NOT NULL, если добавляются строки и явно не предоставляется никакое значение, возвращается сообщение об ошибке. Эти строки добавляются позже как часть обычных действий инструкции INSERT.  
  
## <a name="permissions"></a>Permissions  
 Для выполнения инструкции DROP DEFAULT у пользователя должно быть по крайней мере разрешение ALTER на схему, к которой принадлежит значение по умолчанию.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-dropping-a-default"></a>A. Удаление значения по умолчанию  
 Если значение по умолчанию не привязано к столбцу или псевдониму типа данных, оно может быть удалено при помощи инструкции DROP DEFAULT. В следующем примере удаляется созданное пользователем значение по умолчанию с именем `datedflt`.  
  
```  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT name FROM sys.objects  
         WHERE name = 'datedflt'   
            AND type = 'D')  
   DROP DEFAULT datedflt;  
GO  
```  
  
 Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] можно использовать следующий синтаксис.  
  
```  
DROP DEFAULT IF EXISTS datedflt;  
GO  
```  
  
### <a name="b-dropping-a-default-that-has-been-bound-to-a-column"></a>Б. Удаление значения по умолчанию, привязанного к столбцу  
 В следующем примере отвязывается значения по умолчанию, связанное со столбцом `EmergencyContactPhone` таблицы `Contact`, затем удаляется само значение с именем `phonedflt`.  
  
```  
USE AdventureWorks2012;  
GO  
   BEGIN   
      EXEC sp_unbindefault 'Person.Contact.Phone'  
      DROP DEFAULT phonedflt  
   END;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE DEFAULT (Transact-SQL)](../../t-sql/statements/create-default-transact-sql.md)   
 [sp_helptext (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [sp_help (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [Хранимая процедура sp_unbindefault &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)  
  
  

