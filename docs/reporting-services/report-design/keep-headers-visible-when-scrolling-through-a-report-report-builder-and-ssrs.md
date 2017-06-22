---
title: "Сохранение заголовков видимыми при прокрутке отчета (построитель отчетов и службы SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d9192a4-fd5c-41ad-b9ef-f88f9496afed
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f2fac57fe0e898a1ccbfbe33fb271eae76da1389
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs"></a>Сохранение заголовков видимыми при прокрутке отчета (построитель отчетов и службы SSRS)
  Чтобы предотвратить исчезновение заголовков строк и столбцов из поля видимости при прокрутке после подготовки отчета к просмотру, можно закрепить заголовок строки или столбца.  
  
 Способ управления строками и столбцами зависит от того, используется ли таблица или матрица. Если имеется таблица, то в качестве видимых настраиваются статические элементы (заголовки строк и столбцов). Если же имеется матрица, то в качестве видимых настраиваются заголовки групп строк и столбцов.  
  
 Если вы экспортируете отчет в Excel, заголовок не будет автоматически зафиксирован. Вы можете зафиксировать вкладку в Excel. Дополнительные сведения см. в подразделе **Верхние и нижние колонтитулы страницы** раздела [Экспорт в Microsoft Excel (построитель отчетов и службы SSRS)](../../reporting-services/report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  Даже если в таблице есть группы строк и столбцов, сохранить видимость этих заголовков групп при прокрутке нельзя.  
  
 На следующем рисунке показана таблица.  
  
 ![Таблица](../../reporting-services/report-design/media/table.png "таблицы")  
  
 На следующем рисунке показана матрица.  
  
 ![Матрица](../../reporting-services/report-design/media/matrix.png "матрицы")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-keep-matrix-group-headers-visible-while-scrolling"></a>Сохранение заголовков групп матрицы видимыми при прокрутке  
  
1.  Щелкните правой кнопкой мыши маркер строки или столбца либо угловой маркер области данных табликса, а затем выберите пункт **Свойства табликса**.  
  
2.  На вкладке **Общие** в области **Заголовки строк** или **Заголовки столбцов**установите флажок **Всегда отображать заголовок**.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-keep-a-static-tablix-member-row-or-column-visible-while-scrolling"></a>Сохранение статического элемента табликса (строки или столбца) видимым при прокрутке  
  
1.  В области конструктора щелкните в любом месте таблицы, чтобы открыть статические элементы и группы на панели группирования.  
  
     ![Панель группирования](../../reporting-services/report-design/media/grouppane-updated.png "панель группирования")  
  
     На панели «Группы строк» отображаются иерархические статические и динамические элементы иерархии групп строк, а на панели «Группы столбцов» аналогично отображается иерархия групп столбцов.  
  
2.  В правой части панели группирования щелкните стрелку вниз и нажмите кнопку **Расширенный режим**.  
  
3.  Щелкните статический член (строку или столбец), который нужно оставить видимым при прокрутке. В панели «Свойства» отображаются свойства **Элемент табликса** .  
  
     ![Свойства элемента Табликса](../../reporting-services/report-design/media/grouppane-tablixmember-updated.png "свойства элемента Табликса")  
  
4.  В панели «Свойства» присвойте параметру **FixedData** значение **True**.  
  
5.  Повторите это действие для всех смежных членов, для которых должна сохраняться видимость при прокрутке.  
  
6.  Просмотрите отчет.  
  
 При переходе на страницу вниз или по отчету статические элементы табликса остаются в поле зрения.  
  
## <a name="see-also"></a>См. также раздел  
 [Область данных табликса (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [Поиск, просмотр отчетов и управление ими (построитель отчетов и службы SSRS)](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Экспорт отчетов (построитель отчетов и службы SSRS)](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)   
 [Отображение верхних и нижних колонтитулов в группе (построитель отчетов и службы SSRS)](../../reporting-services/report-design/display-headers-and-footers-with-a-group-report-builder-and-ssrs.md)   
 [Отображение заголовков строк и столбцов на нескольких страницах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md)   
 [Панель группировки (построитель отчетов)](../../reporting-services/report-design/grouping-pane-report-builder.md)  
  
  
