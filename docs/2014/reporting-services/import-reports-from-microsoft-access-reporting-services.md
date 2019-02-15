---
title: Импорт отчетов из Microsoft Access (службы Reporting Services) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Access reports [Reporting Services]
- importing reports
ms.assetid: 4f29d5b8-b77d-4714-a84a-05523df55646
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 7458de1c7424bf3c5b856c263e5180e33e207f76
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56286352"
---
# <a name="import-reports-from-microsoft-access-reporting-services"></a>Импорт отчетов из базы данных Microsoft Access (службы Reporting Services)
  В конструкторе отчетов, можно импортировать отчеты из [!INCLUDE[msCoName](../includes/msconame-md.md)] базы данных Access или project. СУБД Access 2002 или его более поздняя версия должен быть установлен на том же компьютере, что и конструктор отчетов.  
  
 При использовании этой функции выполняется импорт всех отчетов базы данных или проекта. Если файл Access содержит много отчетов, можно создать отдельный проект отчета, в который будет выполняться импорт отчетов, а затем открывать каждый файл на языке определения отчетов в главном проекте отчета. После импорта отчетов в конструктор отчетов их можно изменять.  
  
> [!NOTE]  
>  Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают не все объекты отчетов Access. Отображаются элементы, которые не преобразуются в **список задач** окна. Дополнительные сведения см. в разделе [поддерживаемые функции отчетов Access &#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md).  
  
### <a name="to-import-reports-from-microsoft-access"></a>Импорт отчетов из Microsoft Access  
  
1.  Откройте или создайте проект, в который планируется импортировать отчеты.  
  
2.  На **проекта** последовательно выберите пункты **импортировать отчеты**, а затем нажмите кнопку **Microsoft Access**. Кроме того, щелкните правой кнопкой мыши проект в обозревателе решений, выберите пункт **импортировать отчеты**, а затем нажмите кнопку **Microsoft Access**.  
  
3.  В **откройте** диалоговое окно, выберите базы данных Access (MDB, ACCDB) или проекта (ADP), который содержит отчеты, а затем нажмите кнопку **откройте**. Все отчеты в базе данных или файле проекта импортируются в папку «Отчеты» в обозревателе решений.  
  
4.  Проверьте **список задач** окно для ошибки сборки. Для просмотра **список задач** открытое окно **представление** последовательно выберите пункты **Other Windows**, а затем нажмите кнопку **список задач**.  
  
## <a name="see-also"></a>См. также  
 [Разработка отчетов с использованием конструктора отчетов (SSRS)](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
