---
title: sp_replsetoriginator (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replsetoriginator
- sp_replsetoriginator_TSQL
helpviewer_keywords:
- sp_replsetoriginator
ms.assetid: 030e5226-0585-439f-b8cd-36f48367d86d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5e1f29f06d7a840ed6628ecd4dc193a4f1c54b82
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82817094"
---
# <a name="sp_replsetoriginator-transact-sql"></a>sp_replsetoriginator (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Используется для запуска механизма распознавания замыкания на себя и управления в двунаправленной репликации транзакций. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replsetoriginator [ @server_name= ] 'server_name'   
    , [ @database_name= ] 'database_name'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @server_name = ] 'server_name'`Имя сервера, к которому применяется транзакция. Аргумент *originating_server* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @database_name = ] 'database_name'`Имя базы данных, к которой применяется транзакция. Аргумент *originating_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_replsetoriginator** выполняется агент распространения для записи источника транзакций, применяемых репликацией. Данные сведения используются для запуска механизма распознавания замыкания на себя для двунаправленных транзакционных подписок, которые имеют набор свойств обратной связи.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** на издателе, члены предопределенной роли базы данных **db_owner** в базе данных публикации или пользователи из списка доступа к публикации (PAL) могут выполнять **sp_replsetoriginator**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
