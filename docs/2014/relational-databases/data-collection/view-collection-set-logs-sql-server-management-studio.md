---
title: Просмотр журналов набора элементов сбора (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- logs [SQL Server], viewing
- collection sets [SQL Server], viewing logs
ms.assetid: 428908b8-fb6a-4d0c-8339-ee133e23aad2
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 679fb7b30beed2fd334ce397de15c1398941f288
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095706"
---
# <a name="view-collection-set-logs-sql-server-management-studio"></a>Просмотр журналов набора элементов сбора (среда SQL Server Management Studio)
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
  
## <a name="see-also"></a>См. также  
 [Сбор данных](data-collection.md)   
 [Управление сбором данных](manage-data-collection.md)  
  
  