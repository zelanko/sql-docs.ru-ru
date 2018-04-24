---
title: DROP RULE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 05/11/2017
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP_RULE_TSQL
- DROP RULE
dev_langs:
- TSQL
helpviewer_keywords:
- rules [SQL Server], removing
- deleting roles
- DROP RULE statement
- removing roles
- dropping roles
ms.assetid: 8370b730-7fd5-43fe-a7f6-8300b3caa16d
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aad7cc44fecb5a827d770f79c858fb1d8f25afad
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="drop-rule-transact-sql"></a>DROP RULE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет из текущей базы данных одно или несколько пользовательских правил.  
  
> [!IMPORTANT]  
>  Инструкция DROP RULE будет удалена в следующей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не следует использовать инструкцию DROP RULE при создании новых приложений, и рекомендуется запланировать изменение тех приложений, в которых она используется. Вместо этого следует использовать проверочные ограничения, которые создаются при помощи ключевого слова CHECK в инструкциях [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) и [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md). Дополнительные сведения см. в статье [Ограничения уникальности и проверочные ограничения](../../relational-databases/tables/unique-constraints-and-check-constraints.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DROP RULE [ IF EXISTS ] { [ schema_name . ] rule_name } [ ,...n ] [ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *IF EXISTS*  
 **Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Условное удаление правила только в том случае, если оно уже существует.  
  
 *schema_name*  
 Имя схемы, к которой относится правило.  
  
 *rule*  
 Удаляемое правило. Имена правил должны соответствовать требованиям, предъявляемым к [идентификаторам](../../relational-databases/databases/database-identifiers.md). Указание имени схемы для правил необязательно.  
  
## <a name="remarks"></a>Примечания  
 Если правило привязано к столбцу или псевдониму типа данных, то перед его удалением необходимо удалить привязку при помощи хранимой процедуры **sp_unbindrule**. Если в момент удаления правило привязано, то выводится сообщение об ошибке, и инструкция DROP RULE отменяется.  
  
 После удаления правила новые данные, вводимые в столбцы, ранее управлявшиеся этим правилом, больше им не ограничиваются. На существующие данные удаление правила не влияет.  
  
 Инструкция DROP RULE не применяется к проверочным ограничениям. Дополнительные сведения об удалении ограничений CHECK см. в разделе [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения инструкции DROP RULE пользователь, как минимум, должен иметь разрешение ALTER на схему, которой принадлежит правило.  
  
## <a name="examples"></a>Примеры  
 Следующий пример отменяет привязку и затем удаляет правило с именем `VendorID_rule`. 
  
```  
sp_unbindrule 'Production.ProductVendor.VendorID'  
DROP RULE VendorID_rule  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE RULE (Transact-SQL)](../../t-sql/statements/create-rule-transact-sql.md)   
 [sp_bindrule (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md)   
 [sp_help (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helptext (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [sp_unbindrule (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-unbindrule-transact-sql.md)   
 [USE (Transact-SQL)](../../t-sql/language-elements/use-transact-sql.md)  

