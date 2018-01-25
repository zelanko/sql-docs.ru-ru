---
title: "GET CONVERSATION GROUP (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GET
- CONVERSATION_GROUP_TSQL
- GET_TSQL
- GET_CONVERSATION_GROUP_TSQL
- GET CONVERSATION GROUP
- CONVERSATION GROUP
- GET CONVERSATION
- GET_CONVERSATION_TSQL
dev_langs: TSQL
helpviewer_keywords:
- GET CONVERSATION GROUP statement
- conversations [Service Broker], groups
ms.assetid: 4da8a855-33c0-43b2-a49d-527487cb3b5c
caps.latest.revision: "39"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 04035a9ccbe406b9fa50b5003ab109c3f1ff997d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="get-conversation-group-transact-sql"></a>GET CONVERSATION GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает идентификатор группы сообщений для следующего получаемого сообщения и блокирует группу сообщений для диалога, содержащего сообщение. Идентификатор группы сообщений может использоваться для получения сведений о состоянии диалога до получения непосредственно самого сообщения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
[ WAITFOR ( ]  
   GET CONVERSATION GROUP @conversation_group_id  
      FROM <queue>  
[ ) ] [ , TIMEOUT timeout ]  
[ ; ]  
  
<queue> ::=  
{  
    [ database_name . [ schema_name ] . | schema_name . ] queue_name  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 WAITFOR  
 Указывает, что инструкция GET CONVERSATION GROUP ожидает поступления сообщения в очередь, если в настоящий момент сообщения отсутствуют.  
  
 *@conversation_group_id*  
 Переменная, которая используется для хранения идентификатора группы сообщений, возвращенных инструкцией GET CONVERSATION GROUP. Переменная должна иметь тип **uniqueidentifier**. Если нет доступных групп диалогов, переменной присваивается значение NULL.  
  
 FROM  
 Указывает очередь, из которой должна быть получена группа сообщений.  
  
 *database_name*  
 Имя базы данных, содержащей очередь, из которой должна быть получена группа сообщений. Если аргумент *имя_базы_данных* предоставляется значения по умолчанию для текущей базы данных.  
  
 *schema_name*  
 Имя схемы, владеющей очередью, из которой должна быть получена группа сообщений. Если аргумент *schema_name* указано, по умолчанию используется схема по умолчанию для текущего пользователя.  
  
 *queue_name*  
 Имя очереди, из которой должна быть получена группа сообщений.  
  
 Время ОЖИДАНИЯ *время ожидания*  
 Указывает продолжительность времени (в миллисекундах), в течение которого компонент Service Broker ожидает поступления сообщения в очередь. Это предложение может быть использовано только вместе с предложением WAITFOR. Если инструкция, использующая WAITFOR не содержит это предложение или *время ожидания* равно -1, время ожидания не ограничено. Если время ожидания истекает, GET CONVERSATION GROUP присваивает  *@conversation_group_id*  переменной значение NULL.  
  
## <a name="remarks"></a>Remarks  
  
> [!IMPORTANT]  
>  Если инструкция GET CONVERSATION GROUP не является первой инструкцией в пакете или хранимой процедуре, предыдущая инструкция должна заканчиваться точкой с запятой (**;**), [!INCLUDE[tsql](../../includes/tsql-md.md)] признак конца инструкции.  
  
 Если очередь, указанная в инструкции GET CONVERSATION GROUP, недоступна, инструкция выдает ошибку языка [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Эта инструкция возвращает следующую группу сообщений, для которой верны все, перечисленные ниже, условия:  
  
-   группа сообщений может быть успешно заблокирована;  
  
-   группа сообщений имеет доступные сообщения в очереди;  
  
-   группа сообщений имеет наивысший уровень приоритета среди всех групп сообщений, удовлетворяющих приведенным ранее критериям. Уровень приоритета группы сообщений является самым высоким уровнем приоритета, присвоенным диалогу, являющемуся членом этой группы и имеющему сообщения в очереди.  
  
 Последовательные вызовы инструкций GET CONVERSATION GROUP в пределах одной транзакции могут заблокировать несколько групп сообщений. Если нет доступных групп сообщений, инструкция возвращает значение NULL в качестве идентификатора группы сообщений.  
  
 Если указано предложение WAITFOR, инструкция ожидает либо в течение указанного времени ожидания, либо до появления доступной группы сообщений. Если очередь удаляется в то время как инструкция находится в ожидании, инструкция немедленно возвращает ошибку.  
  
 GET CONVERSATION GROUP недействительна в пользовательской функции.  
  
## <a name="permissions"></a>Разрешения  
 Для получения идентификатора группы сообщений из очереди текущий пользователь должен иметь для очереди разрешение RECEIVE.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-getting-a-conversation-group-waiting-indefinitely"></a>A. Получение группы сообщений, ожидание не определено  
 В следующем примере в качестве значения `@conversation_group_id` используется идентификатор группы сообщений для следующего доступного сообщения в очереди `ExpenseQueue`. Команда ожидает, пока сообщение не станет доступным.  
  
```  
DECLARE @conversation_group_id UNIQUEIDENTIFIER ;  
  
WAITFOR (  
 GET CONVERSATION GROUP @conversation_group_id  
     FROM ExpenseQueue  
) ;  
```  
  
### <a name="b-getting-a-conversation-group-waiting-one-minute"></a>Б. Получение группы сообщений, ожидание — одна минута  
 В следующем примере в качестве значения `@conversation_group_id` используется идентификатор группы сообщений для следующего доступного сообщения в очереди `ExpenseQueue`. Если в течение одной минуты не появится доступного сообщения, инструкция GET CONVERSATION GROUP завершается, не изменяя значение `@conversation_group_id`.  
  
```  
DECLARE @conversation_group_id UNIQUEIDENTIFIER  
  
WAITFOR (  
    GET CONVERSATION GROUP @conversation_group_id   
    FROM ExpenseQueue ),  
TIMEOUT 60000 ;  
```  
  
### <a name="c-getting-a-conversation-group-returning-immediately"></a>В. Получение группы сообщений, немедленное возвращение  
 В следующем примере в качестве значения `@conversation_group_id` используется идентификатор группы сообщений для следующего доступного сообщения в очереди `ExpenseQueue`. Если доступных сообщений нет, инструкция `GET CONVERSATION GROUP` немедленно завершается, не изменяя значение `@conversation_group_id`.  
  
```  
DECLARE @conversation_group_id UNIQUEIDENTIFIER ;  
  
GET CONVERSATION GROUP @conversation_group_id  
FROM AdventureWorks.dbo.ExpenseQueue ;  
```  
  
## <a name="see-also"></a>См. также  
 [BEGIN DIALOG CONVERSATION &#40; Transact-SQL &#41;](../../t-sql/statements/begin-dialog-conversation-transact-sql.md)   
 [ПЕРЕМЕСТИТЬ ДИАЛОГА &#40; Transact-SQL &#41;](../../t-sql/statements/move-conversation-transact-sql.md)  
  
  
