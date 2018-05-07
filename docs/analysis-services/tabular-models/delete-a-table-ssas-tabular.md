---
title: Удаление таблицы | Документы Microsoft
ms.custom: ''
ms.date: 02/22/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: be4ed45f-fde3-466c-9869-49bd3ddb505e
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 981fae53def2e7501d0acb23746db8e7619bc1c7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
  
