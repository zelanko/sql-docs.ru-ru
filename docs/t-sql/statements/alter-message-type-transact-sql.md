---
title: "ИЗМЕНИТЬ тип сообщения (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1ed67afafb33faa22ececbea51c1ed502b1e5725
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-message-type-transact-sql"></a>ALTER MESSAGE TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет свойства типа сообщений.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER MESSAGE TYPE message_type_name  
   VALIDATION =  
    {  NONE   
     | EMPTY   
     | WELL_FORMED_XML   
     | VALID_XML WITH SCHEMA COLLECTION schema_collection_name }  
[ ; ]  
```  
  
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
  
 VALID_XML_WITH_SCHEMA = *данные*  
 Текст сообщения должен содержать XML, который соответствует схеме в указанной коллекции схем. *Данные* должно быть именем существующей коллекции схем XML.  
  
## <a name="remarks"></a>Замечания  
 Изменение проверки типов сообщений не влияет на сообщения, которые уже поставлены в очередь.  
  
 Чтобы изменить параметр AUTHORIZATION для типа сообщений, следует воспользоваться инструкцией ALTER AUTHORIZATION.  
  
## <a name="permissions"></a>Permissions  
 По умолчанию разрешением на изменения типа сообщений обладает владелец типа сообщений, члены **db_ddladmin** или **db_owner** фиксированной роли базы данных и члены **sysadmin**предопределенной роли сервера.  
  
 Если инструкция ALTER MESSAGE TYPE задает коллекцию схемы, пользователь, выполняющий инструкцию, должен иметь разрешение на REFERENCES указанной коллекции схем.  
  
## <a name="examples"></a>Примеры  
 Этот пример изменяет тип сообщений `//Adventure-Works.com/Expenses/SubmitExpense` так, чтобы он требовал наличия в тексте сообщения корректного XML-документа.  
  
```  
ALTER MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/SubmitExpense]  
    VALIDATION = WELL_FORMED_XML ;  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [Создание ТИПА сообщений &#40; Transact-SQL &#41;](../../t-sql/statements/create-message-type-transact-sql.md)   
 [DROP MESSAGE TYPE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-message-type-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
