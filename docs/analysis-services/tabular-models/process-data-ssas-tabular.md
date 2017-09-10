---
title: "Обработки данных (табличные службы SSAS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d88f2dc9-2933-4be5-9bf3-48ffbc2d0a1a
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6fc5d0e934ae7fe4d7f9a00594c2f1ffd21bda1c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="process-data-ssas-tabular"></a>Обработка данных (табличные службы SSAS)
  При импорте данных в табличную модель в режиме кэширования создается моментальный снимок данных на момент импорта. В некоторых случаях эти данные могут оказаться неизменяемыми, и тогда обновлять их в модели не требуется. Однако с большей вероятностью импортированные данные будут регулярно изменяться, поэтому для того, чтобы модель отражала самые актуальные данные из источников данных, необходимо обрабатывать (обновлять) данные и проводить повторный расчет вычисляемых данных. Чтобы обновить данные в модели, выполните действие обработки для всех таблиц, для отдельной таблицы, секции или соединения с источником данных.  
  
 Действия процесса при создании проекта модели необходимо инициировать вручную в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. После развертывания модели операции процесса можно выполнить с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или запланировать с помощью скрипта. Описываемые здесь задачи относятся ко всем действиям процессов, которые можно выполнять во время разработки моделей в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Дополнительные сведения о действиях по обработке для развернутой модели см. в разделе [Обработка базы данных, таблицы или секции (службы Analysis Services)](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Обработка данных вручную (табличные службы SSAS)](../../analysis-services/tabular-models/manually-process-data-ssas-tabular.md)|Описывает обработку данных рабочей области модели вручную.|  
|[Устранение неполадок обработки данных (табличные службы SSAS)](../../analysis-services/troubleshoot-process-data-ssas-tabular.md)|Описывает устранение неполадок при операциях обработки.|  
  
  
