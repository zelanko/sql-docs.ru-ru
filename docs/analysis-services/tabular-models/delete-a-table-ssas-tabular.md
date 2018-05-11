---
title: Удаление таблицы | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1d3176baca80333c8167d45e6fb3a20e85e4f19d
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="delete-a-table"></a>Удаление таблицы
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  В конструкторе моделей разрешено удалять ненужные таблицы из базы данных рабочей области модели. Удаление таблицы не влияет на исходный источник данных. Удаление коснется только данных, которые были импортированы и над которыми велась работа. Удаление таблицы отменить нельзя.  
  
### <a name="to-delete-a-table"></a>Удаление таблицы  
  
-   Щелкните правой кнопкой мыши вкладку в нижней части конструктора моделей для таблицы, которую собираетесь удалить, и выберите команду **Удалить**.  
  
## <a name="considerations-when-deleting-tables"></a>Последствия удаления таблиц  
  
-   При удалении таблицы удаляется и вся вкладка, на которой размещалась эта таблица.  
  
-   Если с таблицей связаны какие-либо меры, то определения мер также будут удалены.  
  
-   Если с помощью этой таблицы были созданы вычисляемые столбцы, столбцы в этой таблице все равно будут удалены, а все вычисляемые столбцы в другой таблице, использующие столбцы удаленной таблицы, отобразят ошибку.  
  
## <a name="see-also"></a>См. также:  
 [Таблицы и столбцы](../../analysis-services/tabular-models/tables-and-columns-ssas-tabular.md)  
  
  
