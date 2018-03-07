---
title: "MOVE CONVERSATION (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
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
- MOVE_CONVERSATION_TSQL
- MOVE CONVERSATION
- MOVE_TSQL
- MOVE
dev_langs:
- TSQL
helpviewer_keywords:
- moving conversations
- MOVE CONVERSATION statement
- relocating conversations
- conversations [Service Broker], groups
- conversations [Service Broker], moving
ms.assetid: 1da4d2c9-e767-434e-b49b-615711a7f626
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cd8c5e548bf45fe4a2fc6bf0638ebb5282981263
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="move-conversation-transact-sql"></a>MOVE CONVERSATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Перемещает диалог в другую группу сообщений.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
MOVE CONVERSATION conversation_handle  
   TO conversation_group_id  
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *conversation_handle*  
 Переменная или константа, содержащая дескриптор перемещаемого диалога. *conversation_handle* должен иметь тип **uniqueidentifier**.  
  
 TO *conversation_group_id*  
 Переменная или константа, содержащая идентификатор группы сообщений, в которую перемещается диалог. *conversation_group_id* должен иметь тип **uniqueidentifier**.  
  
## <a name="remarks"></a>Remarks  
 Инструкция MOVE CONVERSATION Перемещает диалог, указанный аргументом *conversation_handle* к группе сообщений, определяется *conversation_group_id*. Диалоги могут перенаправляться только между группами диалогов, связанными с одной и той же очередью.  
  
> [!IMPORTANT]  
>  Если инструкция MOVE CONVERSATION не является первой инструкцией в пакете или хранимой процедуре, предыдущая инструкция должна заканчиваться точкой с запятой (**;**), [!INCLUDE[tsql](../../includes/tsql-md.md)] признак конца инструкции.  
  
 Инструкция MOVE CONVERSATION блокирует группу сообщений, связанных с *conversation_handle* и группы сообщений, заданные *conversation_group_id* до транзакции содержит оператор фиксации или отката.  
  
 Инструкция MOVE CONVERSATION недопустима в пользовательских функциях.  
  
## <a name="permissions"></a>Разрешения  
 Для перемещения диалога, текущий пользователь должен быть владельцем диалога и группы сообщений, либо членом предопределенной роли сервера sysadmin или предопределенной роли db_owner базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере диалог перемещается в другую группу сообщений.  
  
```  
DECLARE @conversation_handle UNIQUEIDENTIFIER,  
        @conversation_group_id UNIQUEIDENTIFIER ;  
  
SET @conversation_handle =  
    <retrieve conversation handle from database> ;  
SET @conversation_group_id =  
    <retrieve conversation group ID from database> ;  
  
MOVE CONVERSATION @conversation_handle TO @conversation_group_id ;  
```  
  
## <a name="see-also"></a>См. также  
 [BEGIN DIALOG CONVERSATION &#40; Transact-SQL &#41;](../../t-sql/statements/begin-dialog-conversation-transact-sql.md)   
 [GET CONVERSATION GROUP &#40; Transact-SQL &#41;](../../t-sql/statements/get-conversation-group-transact-sql.md)   
 [END CONVERSATION &#40; Transact-SQL &#41;](../../t-sql/statements/end-conversation-transact-sql.md)   
 [sys.conversation_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-conversation-groups-transact-sql.md)   
 [sys.conversation_endpoints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql.md)  
  
  
