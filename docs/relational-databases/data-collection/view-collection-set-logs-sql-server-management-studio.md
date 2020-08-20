---
description: Просмотр журналов набора элементов сбора (среда SQL Server Management Studio)
title: Просмотр журналов набора элементов сбора (SSMS)
ms.date: 06/03/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], viewing
- collection sets [SQL Server], viewing logs
ms.assetid: 428908b8-fb6a-4d0c-8339-ee133e23aad2
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 5974ffeac325fdd3309d18367b0a64aff5086fb4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487247"
---
# <a name="view-collection-set-logs-sql-server-management-studio"></a>Просмотр журналов набора элементов сбора (среда SQL Server Management Studio)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
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
  
  
