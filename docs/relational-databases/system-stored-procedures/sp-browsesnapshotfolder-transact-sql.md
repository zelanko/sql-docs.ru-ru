---
title: sp_browsesnapshotfolder (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_browsesnapshotfolder
- sp_browsesnapshotfolder_TSQL
helpviewer_keywords:
- sp_browsesnapshotfolder
ms.assetid: 0872edf2-4038-4bc1-a68d-05ebfad434d2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 67d4520998dd87c14a817ec05bc14c987e4810a1
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831746"
---
# <a name="sp_browsesnapshotfolder-transact-sql"></a>sp_browsesnapshotfolder (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Возвращает полный путь к последнему моментальному снимку, созданному для данной публикации. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_browsesnapshotfolder [@publication= ] 'publication'  
    { [ , [ @subscriber = ] 'subscriber' ]  
 [ , [ @subscriber_db = ] 'subscriber_db' ] }  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации, содержащей статью. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @subscriber = ] 'subscriber'`Имя подписчика. Аргумент *Subscriber* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'`Имя базы данных подписки. Аргумент *subscriber_db* имеет тип **sysname**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**snapshot_folder**|**nvarchar(512)**|Полный путь к каталогу моментальных снимков.|  
  
## <a name="remarks"></a>Remarks  
 **sp_browsesnapshotfolder** используется в репликации моментальных снимков и репликации транзакций.  
  
 Если поля *подписчика* и *SUBSCRIBER_DB* оставлены пустыми, хранимая процедура возвращает папку моментальных снимков самого последнего моментального снимка, который он может найти для публикации. Если указаны поля *подписчика* и *subscriber_db* , хранимая процедура возвращает папку моментальных снимков для указанной подписки. Если для данной публикации не был создан моментальный снимок, то возвращается пустой результирующий набор.  
  
 Если публикация настроена так, что моментальные снимки создаются и в рабочем каталоге издателя, и в папке моментальных снимков, то результирующий набор состоит из двух строк. Первая строка содержит папку моментальных снимков публикации, а вторая — рабочий каталог издателя. **sp_browsesnapshotfolder** удобно использовать для определения каталога, в котором создаются файлы моментальных снимков.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_browsesnapshotfolder**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
