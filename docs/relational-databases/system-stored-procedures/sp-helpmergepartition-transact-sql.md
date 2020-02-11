---
title: sp_helpmergepartition (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergepartition
- sp_helpmergepartition_TSQL
helpviewer_keywords:
- sp_helpmergepartition
ms.assetid: 184188cc-f519-445d-97ce-aae38f1eb550
author: stevestein
ms.author: sstein
ms.openlocfilehash: 01155b1fb294660c92bfa975bc04de8f748b730f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68137664"
---
# <a name="sp_helpmergepartition-transact-sql"></a>sp_helpmergepartition (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о секции для указанной публикации слиянием. Эта хранимая процедура выполняется на подписчике в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpmergepartition [ @publication= ] 'publication'   
    [ , [ @suser_sname = ] 'suser_sname' ]  
    [ , [ @host_name = ] 'host_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @suser_sname = ] 'suser_sname'`Значение SUSER_SNAME, используемое для определения секции. Аргумент *SUSER_SNAME* имеет тип **sysname**и значение по умолчанию NULL. Введите этот аргумент для ограничения результирующего набора. При этом будут отображаться только те секции, в которых SUSER_SNAME разрешается в указанное значение.  
  
> [!NOTE]  
>  При указании *suser_sname* *HOST_NAME* должен иметь значение null.  
  
`[ @host_name = ] 'host_name'`Значение HOST_NAME, используемое для определения секции. Аргумент *HOST_NAME* имеет тип **sysname**и значение по умолчанию NULL. Введите этот аргумент для ограничения результирующего набора. При этом будут отображаться только те секции, в которых HOST_NAME разрешается в указанное значение.  
  
> [!NOTE]  
>  При указании *suser_sname* *HOST_NAME* должен иметь значение null.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**диска**|**int**|Идентифицирует секцию подписчика.|  
|**host_name**|**имеет sysname**|Значение, используемое при создании секции для подписки, которая фильтруется по значению функции [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) на подписчике.|  
|**suser_sname**|**имеет sysname**|Значение, используемое при создании секции для подписки, которая фильтруется по значению функции [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) на подписчике.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Расположение моментального снимка отфильтрованных данных для секции подписчика.|  
|**date_refreshed**|**datetime**|Дата последнего запуска задания моментального снимка, создающего моментальный снимок отфильтрованных данных для секции.|  
|**dynamic_snapshot_jobid**|**UNIQUEIDENTIFIER**|Идентифицирует задание, которое создает моментальный снимок отфильтрованных данных для секции.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_helpmergepartition** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** и **db_owner** предопределенной роли базы данных могут выполнять **sp_helpmergepartition**.  
  
## <a name="see-also"></a>См. также:  
 [sp_addmergepartition &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md)   
 [sp_dropmergepartition &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql.md)  
  
  
