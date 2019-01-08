---
title: Удаление таблицы в табличной модели служб Analysis Services | Документация Майкрософт
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f47b8eec9642fa9553f6b2e25196b82b38b56a91
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072128"
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
  
## <a name="see-also"></a>См. также  
 [Таблицы и столбцы](../../analysis-services/tabular-models/tables-and-columns-ssas-tabular.md)  
  
  
