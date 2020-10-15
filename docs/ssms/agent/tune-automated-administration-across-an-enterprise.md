---
description: Настройка автоматизированного администрирования в организации
title: Настройка автоматизированного администрирования в организации
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- performance [SQL Server], automated administration
- tuning automated administration [SQL Server]
- monitoring performance [SQL Server], automated administration
ms.assetid: 671fed35-3859-4b0d-8f38-4dd07436857e
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6fbb2e883e77ed797fb367c3624429c2b1a4d720
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92038735"
---
# <a name="tune-automated-administration-across-an-enterprise"></a>Настройка автоматизированного администрирования в организации

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Система многосерверного администрирования с применением агента Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует преимущества средств автоматической настройки, реализованных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Таким образом, в нормальных условиях дополнительная настройка заданий не требуется. Тем не менее при выполнении заданий, формировании предупреждений и уведомлении операторов нагрузка на сеть увеличивается. Чтобы свести к минимуму объем трафика, передаваемого при этих операциях, можно настроить систему автоматизированного администрирования во всей организации.  

## <a name="see-also"></a>См. также:

[Наблюдение за производительностью подсистемы обработки потока данных](../../integration-services/performance/performance-counters.md)