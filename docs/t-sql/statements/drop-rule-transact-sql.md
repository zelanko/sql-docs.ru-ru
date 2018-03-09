---
title: "ПРАВИЛО удаления (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d6ce4daed9a438747765fa4efa90f249425e7c60
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="drop-rule-transact-sql"></a>DROP RULE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет из текущей базы данных одно или несколько пользовательских правил.  
  
> [!IMPORTANT]  
>  DROP RULE будет удалена в следующей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не следует использовать инструкцию DROP RULE при создании новых приложений, и рекомендуется запланировать изменение тех приложений, в которых она используется. Вместо этого используйте ПРОВЕРОЧНЫЕ ограничения, которые можно создавать с помощью ключевого слова CHECK [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) или [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md). Дополнительные сведения см. в статье [Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DROP RULE [ IF EXISTS ] { [ schema_name . ] rule_name } [ ,...n ] [ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *ЕСЛИ СУЩЕСТВУЕТ*  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Условно удаляет правило только в том случае, если он уже существует.  
  
 *schema_name*  
 Имя схемы, к которой относится правило.  
  
 *правило*  
 Удаляемое правило. Имена правил должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md). Указание имени схемы для правил необязательно.  
  
## <a name="remarks"></a>Замечания  
 Если правило привязано к столбцу или псевдониму типа данных, то перед его удалением необходимо удалить привязку Чтобы отменить привязку правила, используйте **sp_unbindrule**. Если в момент удаления правило привязано, то выводится сообщение об ошибке, и инструкция DROP RULE отменяется.  
  
 После удаления правила новые данные, вводимые в столбцы, ранее управлявшиеся этим правилом, больше им не ограничиваются. На существующие данные удаление правила не влияет.  
  
 Инструкция DROP RULE не применяется к проверочным ограничениям. Дополнительные сведения об удалении ПРОВЕРОЧНЫХ ограничений см. в разделе [ALTER TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Для выполнения инструкции DROP RULE пользователь, как минимум, должен иметь разрешение ALTER на схему, которой принадлежит правило.  
  
## <a name="examples"></a>Примеры  
 Следующий пример отменяет привязку и затем удаляет правило с именем `VendorID_rule`. 
  
```  
sp_unbindrule 'Production.ProductVendor.VendorID'  
DROP RULE VendorID_rule  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE RULE (Transact-SQL)](../../t-sql/statements/create-rule-transact-sql.md)   
 [sp_bindrule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md)   
 [sp_help (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helptext (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [sp_unbindrule &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-unbindrule-transact-sql.md)   
 [USE (Transact-SQL)](../../t-sql/language-elements/use-transact-sql.md)  

