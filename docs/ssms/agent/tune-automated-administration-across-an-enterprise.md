---
title: Настройка автоматизированного администрирования в организации | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- performance [SQL Server], automated administration
- tuning automated administration [SQL Server]
- monitoring performance [SQL Server], automated administration
ms.assetid: 671fed35-3859-4b0d-8f38-4dd07436857e
author: markingmyname
ms.author: maghan
manager: jroth
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 671b2e98cf9e9969af68612d75af97bb17984c99
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67681423"
---
# <a name="tune-automated-administration-across-an-enterprise"></a>Настройка автоматизированного администрирования в организации
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Система многосерверного администрирования с применением агента Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует преимущества средств автоматической настройки, реализованных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Таким образом, в нормальных условиях дополнительная настройка заданий не требуется. Тем не менее при выполнении заданий, формировании предупреждений и уведомлении операторов нагрузка на сеть увеличивается. Чтобы свести к минимуму объем трафика, передаваемого при этих операциях, можно настроить систему автоматизированного администрирования во всей организации.  
  
## <a name="see-also"></a>См. также:  
[Наблюдение за производительностью подсистемы обработки потока данных](../../integration-services/performance/performance-counters.md)  
  
