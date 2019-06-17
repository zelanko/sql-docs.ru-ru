---
title: Параметр конфигурации сервера "in-doubt xact resolution" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- distributed transactions [SQL Server], unresolved transactions
- unresolved transactions
- in-doubt xact resolution option
ms.assetid: 3426fd32-cad2-4f2f-8ca9-e0296cc12703
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 648f142eb80607412e13151098418c22e45f04bd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62781940"
---
# <a name="in-doubt-xact-resolution-server-configuration-option"></a>Параметр конфигурации сервера «in-doubt xact resolution»
  Результат по умолчанию для транзакций, которые не удалось разрешить координатору распределенных транзакций **(MS DTC), задается с помощью параметра** in-doubt xact resolution [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Невозможность разрешить транзакции может быть связана с простоем MS DTC или с неизвестным результатом транзакции на момент восстановления.  
  
 В следующей таблице перечислены возможные значения результатов для разрешения сомнительных транзакций.  
  
|Значение результата|Описание|  
|-------------------|-----------------|  
|0|Без предположения. Восстановление завершится неуспешно, если MS DTC не сможет разрешить хотя бы одну сомнительную транзакцию.|  
|1|Предположить фиксацию. Все сомнительные транзакции MS DTC считаются зафиксированными.|  
|2|Предположить прерывание. Все сомнительные транзакции MS DTC считаются прерванными.|  
  
 Чтобы свести к минимуму вероятность увеличения времени простоя, администратор может выбрать с помощью этого параметра либо предположительную фиксацию, либо предположительное прерывание, как показано в приведенном ниже примере.  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 2 -- presume abort  
GO  
RECONFIGURE  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 Кроме того, администратор может не менять значение по умолчанию (без предположения) и допустить сбой восстановления, то есть, как показано в приведенном ниже примере, он будет узнавать о сбое DTC.  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 1 -- presume commit  
GO  
reconfigure  
GO  
ALTER DATABASE pubs SET ONLINE -- run recovery again  
GO  
sp_configure 'in-doubt xact resolution', 0 -- back to no assumptions  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 Параметр **in-doubt xact resolution** является дополнительным. Если для изменения настроек используется системная хранимая процедура **sp_configure** , то изменить значение параметра **in-doubt xact resolution** можно только при условии, что параметр **show advanced options** равен 1. Параметр вступает в силу сразу без перезапуска сервера.  
  
> [!NOTE]  
>  Последовательная настройка этого параметра во всех экземплярах [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые участвуют в распределенных транзакциях, поможет избежать несогласованности данных.  
  
## <a name="see-also"></a>См. также  
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
