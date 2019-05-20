---
title: Решение проблем с ограничениями для строк в Excel 2003 | Документы Майкрософт
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-builder
ms.topic: conceptual
ms.assetid: a4c8700b-bef5-4440-a99c-bba5dcc46bfd
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3898e4202d958c1d20d5436a143e80bb45c7490f
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65577784"
---
# <a name="work-around-the-excel-2003-row-limitation"></a>Work Around the Excel 2003 Row Limitation
  В этом разделе объясняется, как обойти ограничения строк Excel 2003 при экспорте отчетов с разбиением на страницы в Excel. Это решение подходит для отчета, который содержит только таблицу.  
  
> [!IMPORTANT]  
>  Модуль подготовки отчетов [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2003 (XLS) устарел. Дополнительные сведения см. в разделе [Нерекомендуемые функции служб SQL Server Reporting Services в SQL Server 2016](../../reporting-services/deprecated-features-in-sql-server-reporting-services-ssrs.md).  
  
 Excel 2003 поддерживает максимум 65 536 строк на одном листе. Это ограничение можно обойти, реализовав принудительное явное разбиение на страницы после определенного числа строк. Модуль подготовки отчетов Excel создаст новый лист для каждого явного разрыва страницы.  
  
### <a name="to-create-an-explicit-page-break"></a>Создание явного разрыва страницы  
  
1.  Откройте отчет в [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] или на веб-портале [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
2.  Щелкните правой кнопкой мыши строку данных в таблице, а затем выберите **Добавить группу** > **Родительская группа** , чтобы добавить внешнюю группу таблицы.  
  
     ![Выбор родительской группы](../../reporting-services/report-builder/media/datarow-selectparentgroup.png "Выбор родительской группы")  
  
3.  Введите следующую формулу в поле выражения **Группировать по** и нажмите кнопку **ОК** для добавления родительской группы.  
  
     =Int((RowNumber(Nothing)-1)/65000)  
  
     Эта формула назначает номер каждому набору из 65 000 строк в наборе данных. Если для этой группы определен разрыв страницы, данное выражение будет выводить его через каждые 65 000 строк.  
  
     При добавлении внешней группы таблицы в отчет добавляется столбец группы.  
  
4.  Удалите столбец группы, щелкнув правой кнопкой мыши заголовок столбца, затем последовательно выбрав **Удалить столбцы**, **Удалить только столбцы**и нажав кнопку **ОК**.  
  
     ![Удаление столбца группы](../../reporting-services/report-builder/media/groupcolumn-delete-updated.png "Удаление столбца группы")  
  
5.  Щелкните правой кнопкой мыши **группу 1** в разделе **Группы строк** , а затем выберите **Свойства группы**.  
  
     ![Просмотр свойств группы](../../reporting-services/report-builder/media/groupproperties-updated.png "Просмотр свойств группы")  
  
6.  На странице **Сортировка** диалогового окна **Свойства группы** выберите параметр сортировки по умолчанию и нажмите кнопку **Удалить**.  
  
     ![Удаление сортировки по умолчанию](../../reporting-services/report-builder/media/groupproperties-sorting-updated.png "Удаление сортировки по умолчанию")  
  
7.  На странице **Разрывы страниц** щелкните **Между всеми экземплярами группы** , затем нажмите кнопку **ОК**.  
  
     ![Задание разрывов страниц](../../reporting-services/report-builder/media/groupproperties-pagebreaks-updated.png "Задание разрывов страниц")  
  
8.  Сохраните отчет. При экспорте отчета в книгу Excel он размещается на нескольких листах, каждый из которых может содержать не более 65 000 строк.  
  
  
