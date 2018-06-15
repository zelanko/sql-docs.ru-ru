---
title: Параметр конфигурации сервера "in-doubt xact resolution" | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- distributed transactions [SQL Server], unresolved transactions
- unresolved transactions
- in-doubt xact resolution option
ms.assetid: 3426fd32-cad2-4f2f-8ca9-e0296cc12703
caps.latest.revision: 25
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6f8b649548cf2c8182dfa05fe0680c3c4d7b6f94
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32864769"
---
# <a name="in-doubt-xact-resolution-server-configuration-option"></a>Параметр конфигурации сервера «in-doubt xact resolution»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Результат по умолчанию для транзакций, которые не удалось разрешить координатору распределенных транзакций **(MS DTC), задается с помощью параметра** in-doubt xact resolution [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Невозможность разрешить транзакции может быть связана с простоем MS DTC или с неизвестным результатом транзакции на момент восстановления.  
  
 В следующей таблице перечислены возможные значения результатов для разрешения сомнительных транзакций.  
  
|Значение результата|Description|  
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
sp_configure 'in-doubt xact resolution', 2 -– presume abort  
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
sp_configure 'in-doubt xact resolution', 1 -– presume commit  
GO  
reconfigure  
GO  
ALTER DATABASE pubs SET ONLINE –- run recovery again  
GO  
sp_configure 'in-doubt xact resolution', 0 –- back to no assumptions  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 Параметр **in-doubt xact resolution** является дополнительным. Если для изменения настроек используется системная хранимая процедура **sp_configure** , то изменить значение параметра **in-doubt xact resolution** можно только при условии, что параметр **show advanced options** равен 1. Параметр вступает в силу сразу без перезапуска сервера.  
  
> [!NOTE]  
>  Последовательная настройка этого параметра во всех экземплярах [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые участвуют в распределенных транзакциях, поможет избежать несогласованности данных.  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
