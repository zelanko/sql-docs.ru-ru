---
title: Добавление группы подробных сведений (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ef8efba-6d48-4aeb-a3b9-a02ba5a44614
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 5aedacebef1f91a7d7f73e6d1da71bf15bfd8cf9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087317"
---
# <a name="add-a-details-group-report-builder-and-ssrs"></a>Добавление группы подробных сведений (построитель отчетов и службы SSRS)
  Подробные данные из набора данных отчета указываются в виде группы, не содержащей выражение группы. Если необходимо отобразить подробные данные для матрицы, вернуть подробные данные, удаленные из таблицы или списка, или добавить дополнительные группы сведений, то следует добавить дополнительную группу сведений к существующей области данных табликса. Дополнительные сведения о группах см. в разделе [Основные сведения о группах (построитель отчетов и службы SSRS)](understanding-groups-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-details-group-to-a-tablix-data-region"></a>Добавление группы сведений к области данных табликса  
  
1.  В области конструктора щелкните в любом месте области данных табликса, чтобы выделить ее. В панели группирования будут отображены группы столбцов и строк для выбранной области данных.  
  
2.  В панели «Группирование» щелкните правой кнопкой мыши самую внутреннюю дочернюю группу. Нажмите **Добавить группу**и выберите **Дочерняя группа**. Откроется диалоговое окно **Группа табликсов** .  
  
3.  Оставьте поле **Выражение группы**пустым. Группа подробностей не имеет выражения.  
  
4.  Выберите **Показать подробные данные**.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Новая группа подробностей добавляется в панель «Группирование» в виде дочерней группы, и маркер строки для группы, выбранной в шаге 1, отображает значок группы подробностей. Дополнительные сведения о маркерах см. в разделе [Ячейки, строки и столбцы области данных табликса &#40;построитель отчетов&#41; и службы SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>См. также  
 [Добавление или удаление группы в области данных &#40;отчетов построителя отчетов и службы SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)   
 [Общие сведения о группах &#40;отчетов построителя отчетов и службы SSRS&#41;](understanding-groups-report-builder-and-ssrs.md)   
 [Область данных табликса (построитель отчетов и службы SSRS)](../tablix-data-region-report-builder-and-ssrs.md)   
 [Таблицы &#40;построитель отчетов и службы SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [Матрицы &#40;построитель отчетов и службы SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [Списки &#40;построитель отчетов и службы SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  