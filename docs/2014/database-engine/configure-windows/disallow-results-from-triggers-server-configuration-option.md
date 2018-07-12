---
title: Параметр конфигурации сервера "disallow results from triggers" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], result sets
- result sets [SQL Server], triggers
- disallow results from triggers option
ms.assetid: 47149073-307d-47a5-b7d2-66a737d3231d
caps.latest.revision: 28
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 38aa79475f91996230d7e03e111f2839099e7224
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224154"
---
# <a name="disallow-results-from-triggers-server-configuration-option"></a>Параметр конфигурации сервера «disallow results from triggers»
  Параметр **disallow results from triggers** предназначен, чтобы определить, разрешается ли триггерам возвращать результирующие наборы. Триггеры, возвращающие результирующие наборы, могут привести к непредвиденному поведению приложений, не предназначенных для работы с ними.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Рекомендуется установить это значение равным 1.  
  
 При установке в значение 1 параметр **disallow results from triggers** включается (ON). Значение по умолчанию для этого параметра равно 0 (OFF). Если этот параметр равен 1 (ON), любая попытка триггера вернуть результирующий набор завершается неудачей и пользователь получает следующее сообщение об ошибке:  
  
 "Msg 524, уровень 16, состояние 1, процедура \<имя_процедуры>, строка \<номер_строки>  
  
 «Триггер возвратил результирующий набор при параметре сервера "disallow results from triggers", равном True».  
  
 Параметр **disallow results from triggers** применяется на уровне экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , то есть определяет работу всех триггеров, существующих в данном экземпляре.  
  
 Параметр **disallow results from triggers** является дополнительным. Изменить значение этого параметра при помощи системной хранимой процедуры **sp_configure** можно только при условии, если параметр **show advanced options** имеет значение 1. Параметр вступает в силу сразу без перезапуска сервера.  
  
## <a name="see-also"></a>См. также  
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
