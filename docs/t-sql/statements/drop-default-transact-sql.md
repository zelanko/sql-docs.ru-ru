---
title: DROP DEFAULT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 05/10/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 661181e4c8298b2c3e65bf6b022eee718800c118
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81626534"
---
# <a name="drop-default-transact-sql"></a>DROP DEFAULT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет одно или несколько пользовательских значений по умолчанию из текущей базы данных.  
  
> [!IMPORTANT]
>  Инструкция DROP DEFAULT в следующей версии сервера [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет удалена. Не используйте инструкции DROP DEFAULT в новых разработках и запланируйте модификацию приложений, использующих эту инструкцию в настоящее время. Вместо этого используйте определения по умолчанию, которые могут создаваться при помощи ключевого слова DEFAULT инструкций [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) и [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
DROP DEFAULT [ IF EXISTS ] { [ schema_name . ] default_name } [ ,...n ] [ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *IF EXISTS*  
 **Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](https://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Условное удаление таблицы только в том случае, если она уже существует.  
  
 *schema_name*  
 Имя схемы, которой принадлежит значение по умолчанию.  
  
 *default_name*  
 Имя существующего значения по умолчанию. Для просмотра списка значений по умолчанию выполните процедуру **sp_help**. Имена значений по умолчанию должны соответствовать требованиям к именам [идентификаторов](../../relational-databases/databases/database-identifiers.md). Задание имени схемы значения по умолчанию необязательно.  
  
## <a name="remarks"></a>Remarks  
 Перед удалением значения по умолчанию отвяжите его, выполнив процедуру **sp_unbindefault**, если это значение по умолчанию в настоящее время привязано к столбцу или псевдониму типа данных.  
  
 После удаления значения по умолчанию из столбца, в котором допускаются значения NULL, везде на место значения вставляется NULL, если добавляются строки и явно не предоставляется никакое значение. После удаления значения по умолчанию из столбца со свойством NOT NULL, если добавляются строки и явно не предоставляется никакое значение, возвращается сообщение об ошибке. Эти строки добавляются позже как часть обычных действий инструкции INSERT.  
  
## <a name="permissions"></a>Разрешения  
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
  
 Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], можно использовать следующий синтаксис.  
  
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
 [sp_unbindefault (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)  
  
  
