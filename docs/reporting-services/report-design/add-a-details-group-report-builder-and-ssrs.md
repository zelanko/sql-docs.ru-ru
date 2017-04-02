---
title: "Добавление группы подробных сведений (построитель отчетов и службы SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ef8efba-6d48-4aeb-a3b9-a02ba5a44614
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# Добавление группы подробных сведений (построитель отчетов и службы SSRS)
В отчете [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с разбиением на страницы подробные данные из набора данных отчета указываются в виде группы, не содержащей выражение группы. Если необходимо отобразить подробные данные для матрицы, вернуть подробные данные, удаленные из таблицы или списка, или добавить дополнительные группы сведений, то следует добавить дополнительную группу сведений к существующей области данных табликса. Дополнительные сведения о группах см. в разделе [Основные сведения о группах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/understanding-groups-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Добавление группы сведений к области данных табликса  
  
1.  В области конструктора щелкните в любом месте области данных табликса, чтобы выделить ее. В панели группирования будут отображены группы столбцов и строк для выбранной области данных.  
  
2.  В панели «Группирование» щелкните правой кнопкой мыши самую внутреннюю дочернюю группу. Нажмите **Добавить группу**и выберите **Дочерняя группа**. Откроется диалоговое окно **Группа табликсов** .  
  
3.  Оставьте поле **Выражение группы**пустым. Группа подробностей не имеет выражения.  
  
4.  Выберите **Показать подробные данные**.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Новая группа подробностей добавляется в панель «Группирование» в виде дочерней группы, и маркер строки для группы, выбранной в шаге 1, отображает значок группы подробностей. Дополнительные сведения см. в разделе [Ячейки, строки и столбцы области данных табликса (построитель отчетов) и службы SSRS](../../reporting-services/report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).  
  
## См. также  
 [Добавление или удаление группы в области данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)   
 [Основные сведения о группах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/understanding-groups-report-builder-and-ssrs.md)   
 [Область данных табликса (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [Таблицы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-report-builder-and-ssrs.md) 
  [Матрицы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [Списки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)      
 [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  