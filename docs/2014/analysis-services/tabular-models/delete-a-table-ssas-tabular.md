---
title: Удаление таблицы (табличные службы SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: be4ed45f-fde3-466c-9869-49bd3ddb505e
caps.latest.revision: 8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e57cdddbbd7cc4ee75c0758b84d6a68b7fadfd6b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37308494"
---
# <a name="delete-a-table-ssas-tabular"></a>Удаление таблицы (табличные службы SSAS)
  В конструкторе моделей разрешено удалять ненужные таблицы из базы данных рабочей области модели. Удаление таблицы не влияет на исходный источник данных. Удаление коснется только данных, которые были импортированы и над которыми велась работа. Удаление таблицы отменить нельзя.  
  
### <a name="to-delete-a-table"></a>Удаление таблицы  
  
-   Щелкните правой кнопкой мыши вкладку в нижней части конструктора моделей для таблицы, которую собираетесь удалить, и выберите команду **Удалить**.  
  
## <a name="considerations-when-deleting-tables"></a>Последствия удаления таблиц  
  
-   При удалении таблицы удаляется и вся вкладка, на которой размещалась эта таблица.  
  
-   Если с таблицей связаны какие-либо меры, то определения мер также будут удалены.  
  
-   Если с помощью этой таблицы были созданы вычисляемые столбцы, столбцы в этой таблице все равно будут удалены, а все вычисляемые столбцы в другой таблице, использующие столбцы удаленной таблицы, отобразят ошибку.  
  
## <a name="see-also"></a>См. также  
 [Таблицы и столбцы &#40;табличные службы SSAS&#41;](tables-and-columns-ssas-tabular.md)  
  
  
