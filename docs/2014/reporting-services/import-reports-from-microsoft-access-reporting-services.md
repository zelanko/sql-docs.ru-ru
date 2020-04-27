---
title: Импорт отчетов из Microsoft Access (Reporting Services) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Access reports [Reporting Services]
- importing reports
ms.assetid: 4f29d5b8-b77d-4714-a84a-05523df55646
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 862d8b90f3c91dffda35971677db7fdc231c1b63
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108933"
---
# <a name="import-reports-from-microsoft-access-reporting-services"></a>Импорт отчетов из базы данных Microsoft Access (службы Reporting Services)
  В конструктор отчетов можно импортировать отчеты из базы данных или [!INCLUDE[msCoName](../includes/msconame-md.md)] проекта Access. СУБД Access 2002 или его более поздняя версия должен быть установлен на том же компьютере, что и конструктор отчетов.  
  
 При использовании этой функции выполняется импорт всех отчетов базы данных или проекта. Если файл Access содержит много отчетов, можно создать отдельный проект отчета, в который будет выполняться импорт отчетов, а затем открывать каждый файл на языке определения отчетов в главном проекте отчета. После импорта отчетов в конструктор отчетов их можно изменять.  
  
> [!NOTE]  
>  Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают не все объекты отчетов Access. Непреобразованные элементы отображаются в окне **список задач** . Дополнительные сведения см. в разделе [Поддерживаемые функции отчетов Access &#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md).  
  
### <a name="to-import-reports-from-microsoft-access"></a>Импорт отчетов из Microsoft Access  
  
1.  Откройте или создайте проект, в который планируется импортировать отчеты.  
  
2.  В меню **проект** выберите команду **Импорт отчетов**, а затем выберите пункт **Microsoft Access**. Можно также щелкнуть правой кнопкой мыши проект в обозреватель решений, выбрать пункт **Импорт отчетов**, а затем выбрать пункт **Microsoft Access**.  
  
3.  В диалоговом окне **Открыть** выберите базу данных Access (MDB, ACCDB) или проект (ADP), содержащий отчеты, а затем нажмите кнопку **Открыть**. Все отчеты в базе данных или файле проекта импортируются в папку «Отчеты» в обозревателе решений.  
  
4.  Проверьте окно **список задач** на наличие ошибок сборки. Чтобы открыть окно **список задач** , откройте меню **вид** , наведите указатель на пункт **другие окна**, а затем щелкните **список задач**.  
  
## <a name="see-also"></a>См. также  
 [Разработка отчетов с использованием конструктора отчетов (SSRS)](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
