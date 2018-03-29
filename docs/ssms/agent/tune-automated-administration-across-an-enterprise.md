---
title: Настройка автоматизированного администрирования в организации | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance [SQL Server], automated administration
- tuning automated administration [SQL Server]
- monitoring performance [SQL Server], automated administration
ms.assetid: 671fed35-3859-4b0d-8f38-4dd07436857e
caps.latest.revision: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 73af3d205022ed27d137640d374220c3ea8c5129
ms.sourcegitcommit: 34766933e3832ca36181641db4493a0d2f4d05c6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="tune-automated-administration-across-an-enterprise"></a>Настройка автоматизированного администрирования в организации
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Система многосерверного администрирования с применением агента Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] использует преимущества средств автоматической настройки, реализованных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Таким образом, в нормальных условиях дополнительная настройка заданий не требуется. Тем не менее при выполнении заданий, формировании предупреждений и уведомлении операторов нагрузка на сеть увеличивается. Чтобы свести к минимуму объем трафика, передаваемого при этих операциях, можно настроить систему автоматизированного администрирования во всей организации.  
  
## <a name="see-also"></a>См. также:  
[Наблюдение за производительностью подсистемы обработки потока данных](http://msdn.microsoft.com/en-us/11e17f4e-72ed-44d7-a71d-a68937a78e4c)  
  
