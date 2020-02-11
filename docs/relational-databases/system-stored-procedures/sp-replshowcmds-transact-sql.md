---
title: sp_replshowcmds (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replshowcmds
- sp_replshowcmds_TSQL
helpviewer_keywords:
- sp_replshowcmds
ms.assetid: 199f5a74-e08e-4d02-a33c-b8ab0db20f44
author: stevestein
ms.author: sstein
ms.openlocfilehash: 96a32ea04fc53f1a0bf3a842a5e68cde5586ac29
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68770884"
---
# <a name="sp_replshowcmds-transact-sql"></a>sp_replshowcmds (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Возвращает команды для транзакций, отмеченных для репликации, в удобочитаемом формате. **sp_replshowcmds** можно запускать, только если клиентские соединения (включая текущее соединение) не считывают реплицированные транзакции из журнала. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replshowcmds [ @maxtrans = ] maxtrans  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @maxtrans = ] maxtrans`Число транзакций, о которых возвращаются сведения. *maxtrans* имеет **тип int**и значение по умолчанию **1**, указывающее максимальное количество транзакций, ожидающих репликации, для которых **sp_replshowcmds** возвращает сведения.  
  
## <a name="result-sets"></a>Результирующие наборы  
 **sp_replshowcmds** — это диагностическая процедура, которая возвращает сведения о базе данных публикации, из которой она выполняется.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**xact_seqno**|**двоичный (10)**|Последовательный номер команды.|  
|**originator_id**|**int**|Идентификатор инициатора команды, значение всегда **равно 0**.|  
|**publisher_database_id**|**int**|Идентификатор базы данных издателя, значение всегда **равно 0**.|  
|**article_id**|**int**|Идентификатор статьи.|  
|**type**|**int**|Тип команды.|  
|**кнопки**|**nvarchar(1024)**|[!INCLUDE[tsql](../../includes/tsql-md.md)]кнопки.|  
  
## <a name="remarks"></a>Remarks  
 **sp_replshowcmds** используется в репликации транзакций.  
  
 С помощью **sp_replshowcmds**можно просматривать транзакции, которые в настоящее время не распределены (транзакции, оставшиеся в журнале транзакций, которые не были отправлены распространителю).  
  
 Клиенты, выполняющие **sp_replshowcmds** и **sp_replcmds** в одной и той же базе данных, получают ошибку 18752.  
  
 Чтобы избежать этой ошибки, первый клиент должен отключиться или роль клиента в качестве средства чтения журнала, выполнив **sp_replflush**. После отключения всех клиентов от средства чтения журнала **sp_replshowcmds** могут быть успешно выполнены.  
  
> [!NOTE]  
>  **sp_replshowcmds** следует запускать только для устранения неполадок с репликацией.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_replshowcmds**.  
  
## <a name="see-also"></a>См. также:  
 [Сообщения об ошибках](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
