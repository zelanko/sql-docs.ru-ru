---
title: "Удаление таблицы | Документы Microsoft"
ms.custom: 
ms.date: 02/22/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be4ed45f-fde3-466c-9869-49bd3ddb505e
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a4f9c2850798353cb6e16413f395aad1a370a69e
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
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
  
  
