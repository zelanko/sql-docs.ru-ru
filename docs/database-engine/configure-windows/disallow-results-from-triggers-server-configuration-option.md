---
title: Параметр конфигурации сервера "disallow results from triggers" | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], result sets
- result sets [SQL Server], triggers
- disallow results from triggers option
ms.assetid: 47149073-307d-47a5-b7d2-66a737d3231d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 28bf3b201d54798f26c9e887e86a9d0bed78ee15
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68011859"
---
# <a name="disallow-results-from-triggers-server-configuration-option"></a>Параметр конфигурации сервера «disallow results from triggers»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Параметр **disallow results from triggers** предназначен, чтобы определить, разрешается ли триггерам возвращать результирующие наборы. Триггеры, возвращающие результирующие наборы, могут привести к непредвиденному поведению приложений, не предназначенных для работы с ними.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Рекомендуется установить это значение равным 1.  
  
 При установке в значение 1 параметр **disallow results from triggers** включается (ON). Значение по умолчанию для этого параметра равно 0 (OFF). Если этот параметр равен 1 (ON), любая попытка триггера вернуть результирующий набор завершается неудачей и пользователь получает следующее сообщение об ошибке:  
  
 "Msg 524, уровень 16, состояние 1, процедура \<имя_процедуры>, строка \<номер_строки>  
  
 «Триггер возвратил результирующий набор при параметре сервера "disallow results from triggers", равном True».  
  
 Параметр **disallow results from triggers** применяется на уровне экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то есть определяет работу всех триггеров, существующих в данном экземпляре.  
  
 Параметр **disallow results from triggers** является дополнительным. Изменить значение этого параметра при помощи системной хранимой процедуры **sp_configure** можно только при условии, если параметр **show advanced options** имеет значение 1. Параметр вступает в силу сразу без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
