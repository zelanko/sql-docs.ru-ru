---
title: "Занятие 2: Указание сведений о соединении (службы Reporting Services) | Документы Microsoft"
ms.custom: 
ms.date: 05/23/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
caps.latest.revision: 53
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 4d0667dec1b59d5560ca24176634dddc5d6d8d18
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>Занятие 2. Задание информации о соединении (службы Reporting Services)
После добавления [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] разбиением на страницы отчета в проект Tutorial на занятии 1, теперь вам необходимо определить *источника данных*, который является сведения о соединении, отчет использует для доступа к данным из реляционной базы данных, многомерные базы данных или другого источника.  
  
На этом занятии использовать [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] образца базы данных в качестве источника данных. В этом учебнике предполагается, что эта база данных находится в экземпляр по умолчанию [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] установлен на локальном компьютере.  
  
### <a name="to-set-up-a-connection"></a>Настройка соединения  
  
1.  В области **данных отчета** нажмите кнопку **Создать** и выберите **Data Source**.  
Если область **Данные отчета** не отображается, в меню **Вид** выберите пункт **Данные отчета**.  

    ![SSRS-Table-Tutorial-2-New-Data-Source](../reporting-services/media/ssrs-table-tutorial-2-new-data-source.png)
  
   2.  В поле **Имя**введите *AdventureWorks2014*.  
  
3.  Убедитесь в том, что выбран параметр **Внедренное соединение** .  
  
4.  В поле **Тип**выберите **Microsoft SQL Server**.  
  
5.  В поле **Строка подключения**введите следующее:  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2014  
    ```  
  
     Эта строка соединения подразумевает, что на локальном компьютере установлены среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], сервер отчетов и база данных [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] , а у пользователя имеется разрешение на подключение к базе данных [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] . Если базы данных AdventureWorks2014 не на локальном компьютере, измените строку подключения и замените *localhost* с именем экземпляра сервера базы данных.
  
     >[!NOTE]  
    >В случае использования версии [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services или именованного экземпляра строка соединения должна включать сведения об экземпляре:  
    >  
    >`Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2014`  
    >  
    >Дополнительные сведения о строках подключения см. в следующих разделах: [Data Connections, Data Sources, and Connection Strings in Reporting Services](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
     
  
6.  На панели слева щелкните **Учетные данные** и выберите **Использовать проверку подлинности Windows (встроенная безопасность)**.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)] Источник данных **AdventureWorks2014** появляется в области **данных отчета** .  
![ssrs_adventureworks_datasource](../reporting-services/media/ssrs-adventureworks-datasource.png)  
## <a name="next-task"></a>Следующая задача  
Соединение с образцом базы данных [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] успешно создано. Далее предстоит создать отчет. В разделе [Lesson 3: определение набора данных для табличного отчета &#40; Службы Reporting Services &#41; ](../reporting-services/lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md).  
  
## <a name="see-also"></a>См. также:  
[Data Connections, Data Sources, and Connection Strings in Reporting Services](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
  
  
  


