---
description: Хранимая процедура sp_dropmergealternatepublisher (Transact-SQL)
title: sp_dropmergealternatepublisher (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergealternatepublisher
- sp_dropmergealternatepublisher_TSQL
helpviewer_keywords:
- sp_dropmergealternatepublisher
ms.assetid: a7dee4e2-2a60-41da-9d1d-6f991d7e2c5e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: feaecea81d5d92cfa5fb8e5bf171edc6ea05d99d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481316"
---
# <a name="sp_dropmergealternatepublisher-transact-sql"></a>Хранимая процедура sp_dropmergealternatepublisher (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет альтернативный издатель из публикации слиянием. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropmergealaternatepublisher [ @publisher = ] 'publisher'    , [ @publisher_db = ] 'publisher_db'    , [ @publication = ] 'publication'    , [ @alternate_publisher = ] 'alternate_publisher'    , [ @alternate_publisher_db = ] 'alternate_publisher_db'    , [ @alternate_publication = ] 'alternate_publication'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'` Имя текущего издателя. параметр *Publisher*имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'` Имя текущей базы данных публикации. Аргумент *publisher_db*имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publication = ] 'publication'` Имя текущей публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @alternate_publisher = ] 'alternate_publisher'` Имя альтернативного издателя, который следует удалить в качестве альтернативного участника синхронизации. Аргумент *alternate_publisher*имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @alternate_publisher_db = ] 'alternate_publisher_db'` Имя базы данных публикации, которая будет удалена в качестве альтернативной базы данных публикации партнера по синхронизации. Аргумент *alternate_publisher_db*имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @alternate_publication = ] 'alternate_publication'` Имя публикации, которую нужно удалить в качестве альтернативной публикации партнера синхронизации. Аргумент *alternate_publication*имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_dropmergealternatepublisher** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_dropmergelternatepublisher**.  
  
## <a name="see-also"></a>См. также  
 [sp_addmergealternatepublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergealternatepublisher-transact-sql.md)  
  
  
