---
title: sp_delete_log_shipping_secondary_primary (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_log_shipping_secondary_primary_TSQL
- sp_delete_log_shipping_secondary_primary
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_log_shipping_secondary_primary
ms.assetid: 507fc744-73d9-4cb7-8d2a-bcff88841c6a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 654438872c4f202f8406bc035f0371f6ace536c9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750580"
---
# <a name="sp_delete_log_shipping_secondary_primary-transact-sql"></a>sp_delete_log_shipping_secondary_primary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Эта хранимая процедура удаляет сведения об указанном сервере-источнике с сервера-получателя, а также удаляет задание копирования и задание восстановления с сервера-получателя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_log_shipping_secondary_primary  
[ @primary_server = ] 'primary_server'  
[ @primary_database = ] 'primary_database'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @primary_server = ] 'primary_server'`Имя основного экземпляра в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] конфигурации доставки журналов. *primary_server* имеет тип **sysname** и не может иметь значение null.  
  
`[ @primary_database = ] 'primary_database'`Имя базы данных на сервере-источнике. Аргумент *primary_database* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет.  
  
## <a name="remarks"></a>Примечания  
 **sp_delete_log_shipping_secondary_primary** должны запускаться из базы данных **master** на сервере-получателе. Эта хранимая процедура выполняет следующее:  
  
1.  Удаляет задания копирования и восстановления для вторичного идентификатора.  
  
2.  Удаляет запись в **log_shipping_secondary**.  
  
3.  Вызывает **sp_delete_log_shipping_alert_job** на сервере мониторинга.  
  
## <a name="permissions"></a>Разрешения  
 Эту процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** .  
  
## <a name="see-also"></a>См. также:  
 [Сведения о доставке журналов (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
