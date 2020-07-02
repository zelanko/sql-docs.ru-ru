---
title: sp_dropdistributiondb (Transact-SQL) | Документация Майкрософт
description: Удаляет базу данных распространителя и используемые ею файлы, если они не используются другой базой данных. Эта хранимая процедура выполняется на распространителе в любой базе данных.
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropdistributiondb_TSQL
- sp_dropdistributiondb
helpviewer_keywords:
- sp_dropdistributiondb
ms.assetid: b6dd1846-2259-4d29-93af-a70a5d25a0c5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9d9290b02c149889a488452d71ae800134d38f00
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786968"
---
# <a name="sp_dropdistributiondb-transact-sql"></a>sp_dropdistributiondb (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Сбрасывает базу данных распространителя. Сбрасывает физические файлы, используемые базой данных, если они не используются другой базой данных. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropdistributiondb [ @database= ] 'database'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @database = ] 'database'`Удаляемая база данных. Аргумент *Database* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_dropdistributiondb** используется во всех типах репликации.  
  
 Эту хранимую процедуру необходимо выполнить перед удалением распространителя, выполнив **sp_dropdistributor**.  
  
 **sp_dropdistributiondb** также удаляет задание агент чтения очереди для базы данных распространителя, если оно существует.  
  
 Чтобы отключить распространение, база данных распространителя должна быть в режиме «в сети». Если для базы данных распространителя существует моментальный снимок базы данных, он должен быть сброшен перед отключением распространения. Моментальный снимок базы данных доступен только для чтения в виде копии базы данных вне сети и не относится к моментальному снимку репликации. Дополнительные сведения см. в разделе [Моментальные снимки базы данных (SQL Server)](../../relational-databases/databases/database-snapshots-sql-server.md).  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_DropDistPub](../../relational-databases/replication/codesnippet/tsql/sp-dropdistributiondb-tr_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_dropdistributiondb**.  
  
## <a name="see-also"></a>См. также  
 [Отключение публикации и распространения](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [sp_adddistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)   
 [sp_changedistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md)   
 [sp_helpdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
