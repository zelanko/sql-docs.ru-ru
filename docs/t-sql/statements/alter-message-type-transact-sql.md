---
description: ALTER MESSAGE TYPE (Transact-SQL)
title: ALTER MESSAGE TYPE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER_MESSAGE_TYPE_TSQL
- ALTER MESSAGE TYPE
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER MESSAGE TYPE statement
- modifying message types
- message types [Service Broker], modifying
ms.assetid: 98c94176-2bdf-4725-b4bc-d33b6b14817d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 25553c83a9d564be0ea2ef6a5bb845c750d4f589
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444920"
---
# <a name="alter-message-type-transact-sql"></a>ALTER MESSAGE TYPE (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  Изменяет свойства типа сообщений.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
  
ALTER MESSAGE TYPE message_type_name  
   VALIDATION =  
    {  NONE   
     | EMPTY   
     | WELL_FORMED_XML   
     | VALID_XML WITH SCHEMA COLLECTION schema_collection_name }  
[ ; ]  
```  
  

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *message_type_name*  
 Имя изменяемого типа сообщений. Не могут быть указаны имена сервера, базы данных и схемы.  
  
 VALIDATION  
 Указывает, как компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] производит проверку текста сообщения этого типа.  
  
 None  
 Проверка не произведена. Текст сообщения может содержать любые данные или иметь значение NULL.  
  
 EMPTY  
 Тело сообщения должно быть значением NULL.  
  
 WELL_FORMED_XML  
 Тело сообщения должно содержать корректные XML-данные.  
  
 VALID_XML_WITH_SCHEMA = *schema_collection_name*  
 Текст сообщения должен содержать XML, который соответствует схеме в указанной коллекции схем. Аргумент *schema_collection_name* должен быть именем существующей коллекции XML-схем.  
  
## <a name="remarks"></a>Remarks  
 Изменение проверки типов сообщений не влияет на сообщения, которые уже поставлены в очередь.  
  
 Чтобы изменить параметр AUTHORIZATION для типа сообщений, следует воспользоваться инструкцией ALTER AUTHORIZATION.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешением на изменения типа сообщений обладает владелец типа сообщений, члены предопределенной роли базы данных **db_ddladmin** или **db_owner** и члены предопределенной роли сервера **sysadmin**.  
  
 Если инструкция ALTER MESSAGE TYPE задает коллекцию схемы, пользователь, выполняющий инструкцию, должен иметь разрешение на REFERENCES указанной коллекции схем.  
  
## <a name="examples"></a>Примеры  
 Этот пример изменяет тип сообщений `//Adventure-Works.com/Expenses/SubmitExpense` так, чтобы он требовал наличия в тексте сообщения корректного XML-документа.  
  
```  
ALTER MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/SubmitExpense]  
    VALIDATION = WELL_FORMED_XML ;  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER AUTHORIZATION (Transact-SQL)](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [CREATE MESSAGE TYPE (Transact-SQL)](../../t-sql/statements/create-message-type-transact-sql.md)   
 [DROP MESSAGE TYPE (Transact-SQL)](../../t-sql/statements/drop-message-type-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
