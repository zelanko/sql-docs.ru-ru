---
title: sp_addmergepartition (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepartition
- sp_addmergepartition_TSQL
helpviewer_keywords:
- sp_addmergepartition
ms.assetid: 02a5f46b-e5ff-4932-a3ff-7f0fd82d0981
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a4f4743efbd0ee3b7a57cb4fab02c98a2680a870
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786271"
---
# <a name="sp_addmergepartition-transact-sql"></a>sp_addmergepartition (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Создает динамически фильтруемую секцию для подписки, которая фильтруется по значениям [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) или [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) на подписчике. Данная хранимая процедура выполняется на издателе публикуемой базы данных и используется для создания секций вручную.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addmergepartition [ @publication = ] 'publication'  
        , [ @suser_sname = ] 'suser_sname'  
        , [ @host_name = ] 'host_name'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Публикация слиянием, в которой создается секция. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию. Если указан параметр *SUSER_SNAME* , значение *HostName* должно быть равно null.  
  
`[ @suser_sname = ] 'suser_sname'`Значение, используемое при создании секции для подписки, которая фильтруется по значению функции [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) на подписчике. Аргумент *SUSER_SNAME* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @host_name = ] 'host_name'`Значение, используемое при создании секции для подписки, которая фильтруется по значению функции [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) на подписчике. Аргумент *HOST_NAME* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_addmergepartition** используется в репликации слиянием.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_MergeDynamicPubPlusPartition](../../relational-databases/replication/codesnippet/tsql/sp-addmergepartition-tra_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_addmergepartition**.  
  
## <a name="see-also"></a>См. также  
 [Создание моментального снимка для публикации слиянием с параметризованными фильтрами](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)   
 [Параметризованные фильтры строк](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)  
  
  
