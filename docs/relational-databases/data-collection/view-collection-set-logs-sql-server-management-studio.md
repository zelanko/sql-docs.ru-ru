---
title: "Просмотр журналов набора элементов сбора (среда SQL Server Management Studio) | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: data-collection
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logs [SQL Server], viewing
- collection sets [SQL Server], viewing logs
ms.assetid: 428908b8-fb6a-4d0c-8339-ee133e23aad2
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dd98e2f24464fb9c5fc38782803768530e7f94ec
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="view-collection-set-logs-sql-server-management-studio"></a>Просмотр журналов набора элементов сбора (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Просмотреть журналы набора сбора, все сразу или по отдельности, можно в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
### <a name="to-view-collection-set-logs"></a>Просмотр журналов набора сбора  
  
1.  В обозревателе объектов раскройте папку **Управление** .  
  
2.  Щелкните правой кнопкой мыши **Сбор данных**и выберите пункт **Просмотр журналов**.  
  
     При этом открывается **средство просмотра журнала**. Все файлы журнала для каждого набора сбора будут перечислены и предварительно выбраны в узле **Сбор данных** .  
  
3.  Для просмотра журналов только определенных наборов сбора снимите флажки рядом с каждым набором сбора, журналы которых просматривать нет необходимости. Сведения о журнале для этих наборов сбора будут удалены из панели данных **средства просмотра файлов журнала** .  
  
### <a name="to-view-a-specific-collection-set-log-file"></a>Просмотр определенного файла журнала набора сбора  
  
1.  В обозревателе объектов разверните папку **Управление** , затем узел **Сбор данных**.  
  
2.  Щелкните правой кнопкой мыши набор сбора, журнал которого нужно просмотреть, и выберите пункт **Просмотр журналов**.  
  
     Откроется **средство просмотра файлов журнала** , отображающий файл журнала только для выбранного набора сбора.  
  
## <a name="see-also"></a>См. также:  
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)   
 [Управление сбором данных](../../relational-databases/data-collection/manage-data-collection.md)  
  
  
