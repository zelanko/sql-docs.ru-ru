---
title: "Извлечение рефлексивных связей (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing reflexive relationships
- reflexive relationships
- database diagrams [SQL Server], relationships
ms.assetid: e218363f-faec-46d5-9904-a537fbcc994d
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 56b5d0c6558b802d595eee6cb6e3a2e0acabcbec
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="draw-reflexive-relationships-visual-database-tools"></a>Извлечение рефлексивных связей (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Чтобы связать столбец или столбцы в таблице с другим столбцом или столбцами в той же таблице, можно создать рефлексивные связи. Например, в таблице `employee` имеется столбец `emp_id` и столбец `mgr_id` . Учитывая то, что менеджеры также являются сотрудниками, можно связать эти столбцы при помощи линии взаимосвязи в таблице. Такие связи гарантируют, что каждый идентификатор менеджера, добавляемый в таблицу, будет соответствовать существующему идентификатору сотрудника.  
  
Перед тем как создавать связи, необходимо определить для таблицы первичный ключ или ограничение уникальности. Затем необходимо связать первичный ключевой столбец с соответствующим столбцом. После того как связь создана, соответствующий столбец становится внешним ключом таблицы.  
  
### <a name="to-draw-a-reflexive-relationship"></a>Извлечение рефлексивной связи  
  
1.  В диаграмме базы данных щелкните переключатель строк для столбца базы данных, который необходимо связать с другим столбцом, и перетаскивайте указатель за пределы таблицы, пока не появится линия.  
  
2.  Перетащите линию назад к выбранной таблице.  
  
3.  Отпустите кнопку мыши. Появится диалоговое окно **Таблицы и столбцы** .  
  
4.  Выберите ключевой столбец внешнего ключа и таблицу первичного ключа, с которой необходимо установить связь.  
  
5.  Дважды нажмите кнопку **ОК** , чтобы создать связь.  
  
При выполнении запросов в таблице для создания самосоединения можно использовать рефлексивные связи. Дополнительные сведения о запросах к таблицам с соединениями см. в разделе [Запросы с соединениями (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md).  
  
## <a name="see-also"></a>См. также:  
[Запросы с соединениями (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
