---
title: Параметр конфигурации сервера "in-doubt xact resolution" | Документы Майкрософт
description: Описание параметра in-doubt xact resolution. Сведения о том, как он определяет результат по умолчанию для сомнительных транзакций в SQL Server.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- distributed transactions [SQL Server], unresolved transactions
- unresolved transactions
- in-doubt xact resolution option
ms.assetid: 3426fd32-cad2-4f2f-8ca9-e0296cc12703
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 946f36bb379e5fde01f4232b01699405dd63aa8d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772421"
---
# <a name="in-doubt-xact-resolution-server-configuration-option"></a>Параметр конфигурации сервера «in-doubt xact resolution»
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
