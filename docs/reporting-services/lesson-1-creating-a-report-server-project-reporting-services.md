---
title: "Урок 1: Создание проекта сервера отчетов (службы Reporting Services) | Документы Microsoft"
ms.custom: 
ms.date: 11/30/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 675671ca-e6c9-48a2-82e9-386778f3a49f
caps.latest.revision: 57
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 6292a812cb1456892a6dad78408d0d64ce0b1a9e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/27/2017

---
# <a name="lesson-1-creating-a-report-server-project-reporting-services"></a>Занятие 1. Создание проекта сервера отчетов (службы Reporting Services)

 > Содержимое, связанное с предыдущих версий SQL Server, в разделе [занятия 1: Создание проекта сервера отчетов (службы Reporting Services)](https://msdn.microsoft.com/en-US/library/ms167559(SQL.120).aspx).

На этом занятии вы создадите *проект сервера отчетов* и *RDL-файл определения отчета* в [!INCLUDE[ssBIDevStudio_md](../includes/ssbidevstudio-md.md)] в среде Visual Studio. 

Чтобы создать отчет в [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], нужно сначала создать проект сервера отчетов, в котором можно сохранить файл определения отчета (с расширением RDL) и другие файлы ресурсов, необходимые для отчета. 

На следующих занятиях вы определите источник данных, набор данных и макет для этого отчета. При выполнении отчета происходит получение и объединение данных с макетом, а затем осуществляется его подготовка к просмотру на экране. После этого отчет можно экспортировать, распечатать или сохранить.  
  
  
  
## <a name="to-create-a-report-server-project"></a>Создание проекта сервера отчетов  
  
1.  Откройте среду [!INCLUDE[ssBIDevStudio_md](../includes/ssbidevstudio-md.md)].  
  
2.  На **файл** меню > **New** > **проекта**.  

    ![ssrs-ssdt-file-01-new-project](../reporting-services/media/ssrs-ssdt-file-01-new-project.png)
  
3.  В разделе **Установленные** > **Шаблоны** > **Business Intelligence**(Бизнес-аналитика) щелкните **Службы отчетов**.

    ![ssrs-ssdt-01-new-rs-project](../reporting-services/media/ssrs-ssdt-01-new-rs-project.png)

5. Щелкните **Проект сервера отчетов** ![ssrs_ssdt_report_server_project](../reporting-services/media/ssrs-ssdt-report-server-project.png). 

   >**Примечание**: Если вы не видите **бизнес-аналитики** или **проекта сервера отчетов** параметры, необходимо обновить SSDT с помощью шаблонов бизнес-аналитики. См. страницу [Скачать SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md).  
  
5.  В поле **Имя**введите **Руководство**.  

    По умолчанию он создается в папке Visual Studio 2015\Projects в новом каталоге.
    
    ![ssrs-ssdt-01-solution-location](../reporting-services/media/ssrs-ssdt-01-solution-location.png)
  
6.  Чтобы создать проект, нажмите кнопку **ОК** .  
  
    Проект "Руководство" отобразится в области обозревателя решений справа.  
  
## <a name="to-create-a-new-report-definition-file"></a>Создание файла определения отчета  
  
1.  В области **обозревателя решений** щелкните правой кнопкой мыши **Отчеты** > **Добавить** > **Новый элемент**. 

    >**Совет.**Если область **обозревателя решений** не отображается, в меню **Вид** выберите пункт **Обозреватель решений**. 

    ![ssrs_ssdt_add_report](../reporting-services/media/ssrs-ssdt-add-report.png)
  
2.  В окне **Добавление нового элемента** щелкните **Отчет** ![ssrs_ssdt_report](../reporting-services/media/ssrs-ssdt-report.png).  
  
3.  В поле **Имя**введите **Sales Orders.rdl** и нажмите кнопку **Добавить**.  
  
    Конструктор отчетов откроет и отобразит новый RDL-файл в конструкторе.  
    
    ![ssrs-ssdt-01-new-report-designer](../reporting-services/media/ssrs-ssdt-01-new-report-designer.png)
  
     Конструктор отчетов является компонентом служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , запускаемым в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Он имеет два представления: **Конструктор** и **Предварительный просмотр**. Смена представлений осуществляется посредством выбора вкладок.  
  
    Данные определяются в области **Данные отчета** . Макет отчета определяется в представлении **Конструктор** . Отчет можно выполнить и посмотреть, как он выглядит, в представлении **Предварительный просмотр** .  
  
## <a name="next-lesson"></a>Следующее занятие  
Создание проекта отчета с именем «Учебник» и добавление в него файла определения отчета (с расширением RDL) успешно завершено. Далее требуется определить источник данных, который будет использован в отчете. В разделе [уроке 2: Указание сведений о соединении &#40; Службы Reporting Services &#41; ](../reporting-services/lesson-2-specifying-connection-information-reporting-services.md).  
  
## <a name="see-also"></a>См. также:  
[Создание простого табличного отчета (учебник по службам SSRS)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  
  


