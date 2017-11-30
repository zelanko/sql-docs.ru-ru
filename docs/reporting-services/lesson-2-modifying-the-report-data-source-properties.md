---
title: "Занятие 2. Изменение свойств источника данных отчета | Документы Майкрософт"
ms.custom: 
ms.date: 05/23/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: c962b0ff-ce8a-4742-8262-dc730901afcf
caps.latest.revision: "43"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 9a2e755b3aa71ba3792b5be5aa72367a0e218215
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="lesson-2-modifying-the-report-data-source-properties"></a>Lesson 2: Modifying the Report Data Source Properties
На этом занятии учебника по службам [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] с помощью веб-портала будет выбран отчет, который необходимо доставить получателям. Управляемая данными подписка, которую вы создадите, будет распространять отчет **Заказ на продажу** , созданный при работе с учебником [Создание простого табличного отчета (учебник по службам SSRS)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md).  В последующих шагах будут изменены сведения о соединении с источником данных, используемые в отчете для получения данных. Только отчеты, использующие **сохраненные учетные данные** для доступа к источнику данных для отчета, могут распространяться с помощью управляемой данными подписки. Сохраненные учетные данные нужны для автоматической обработки отчета.  
  
Вы также измените набор данных и отчет, включив в них параметр для фильтрации отчета по `[Order]` , с тем чтобы подписка могла выдавать разные экземпляры отчета для определенных заказов и форматов подготовки к просмотру.  
  
## <a name="bkmk_modify_datasource"></a>Изменение источника данных для использования сохраненных учетных данных  
  
1.  Перейдите на веб-портал [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] с правами администратора. Например, щелкните значок Internet Explorer правой кнопкой мыши и выберите пункт **Запуск от имени администратора**.  
 
2.    Перейдите по URL-адресу веб-портала.  Например:   
    `http://<server name>/reports`.  
    `http://localhost/reports`
 **Примечание** . URL-адресом веб- *портала* является "Reports", но URL-адресом *сервера* отчетов не является "Reportserver".  
3.  Перейдите в папку с отчетом **Sales Orders** и в контекстном меню отчета щелкните пункт **Управление**.  
 
 ![ssrs_tutorial_datadriven_manage_report](../reporting-services/media/ssrs-tutorial-datadriven-manage-report.png)
  
3.  В области слева щелкните **Источники данных** .  
  
4.  В поле **Тип подключения** должно быть выбрано значение **Microsoft SQL Server**.  
  
5.  Проверьте, имеет ли строка подключения следующий вид (предполагается, что образец базы данных находится на локальном сервере базы данных):  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2014  
    ```  
  
6.  Выберите **С использованием этих учетных данных**.  
  
7. В списке **Тип учетных данных**выберите значение **Пароль и имя пользователя Windows**
8. Введите имя пользователя (в формате *домен\имя*) и пароль. Воспользуйтесь именем входа, у которого есть разрешение на доступ к базе данных AdventureWorks2014.  
    
9. Нажмите кнопку **Проверить соединение** , чтобы проверить соединение с источником данных.  
  
10. Нажмите кнопку **Сохранить**.
11. Нажмите кнопку **Отмена**.  
  
11. Просмотрите отчет, чтобы убедиться, что он выполняется с указанными учетными данными. .  
  
## <a name="bkmk_modify_dataset"></a>Изменение набора данных AdventureWorksDataset  
 В последующих шагах вы измените набор данных так, чтобы использовался параметр для фильтрации набора данных по номеру заказа.
1.  Откройте отчет **Заказы на продажу** в среде [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]  
  
2.  Щелкните правой кнопкой мыши набор данных `AdventureWorksDataset` и выберите пункт **Свойства набора данных**.  
    ![ssrs_tutorial_datadriven_datasetproperties](../reporting-services/media/ssrs-tutorial-datadriven-datasetproperties.png)  
3.  Добавьте инструкцию `WHERE (UPPER(SalesOrderNumber) =UPPER(@OrderNumber) or  @OrderNumber IS NULL)` перед инструкцией `Group By` . Полный синтаксис запроса:  
  
    ```  
    SELECT soh.OrderDate AS Date, soh.SalesOrderNumber AS [Order], pps.Name AS Subcat, pp.Name AS Product, SUM(sd.OrderQty) AS Qty, SUM(sd.LineTotal)  AS LineTotal  
    FROM Sales.SalesPerson AS sp INNER JOIN  
      Sales.SalesOrderHeader AS soh ON sp.BusinessEntityID = soh.SalesPersonID INNER JOIN  
       Sales.SalesOrderDetail AS sd ON sd.SalesOrderID = soh.SalesOrderID INNER JOIN  
       Production.Product AS pp ON sd.ProductID = pp.ProductID  
    INNER JOIN  
       Production.ProductSubcategory AS pps ON pp.ProductSubcategoryID = pps.ProductSubcategoryID   
    INNER JOIN  
        Production.ProductCategory AS ppc ON ppc.ProductCategoryID = pps.ProductCategoryID  
  
    WHERE (UPPER(SalesOrderNumber) =UPPER(@OrderNumber) or  @OrderNumber IS NULL)  
  
    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name, soh.SalesPersonID  
    HAVING (ppc.Name = 'Clothing')  
    ```  
  
4.  Нажмите кнопку **ОК**.  
 В последующих шагах вы добавите параметр к отчету.  Значение из параметра отчета передается в параметр набора данных. 
## <a name="bkmk_add_reportparameter"></a>Добавление параметра отчета и повторная публикация отчета  
  
1.  В области **Данные отчета** разверните папку параметров и дважды щелкните параметр **Ordernumber** .  Он был создан автоматически в ходе выполнения предыдущих действий по добавлению параметра к набору данных. Нажмите кнопку **Создать** и выберите пункт **Параметр...**  
 ![ssrs_tutorial_datadriven_parameter](../reporting-services/media/ssrs-tutorial-datadriven-parameter.png) 
2.  Поле **Имя** должно содержать значение `OrderNumber`.  
  
3.  Поле **Подсказка** должно содержать значение `OrderNumber`.  
  
4.  Выберите **Разрешить пустое значение ("")**.  
  
5.  Выберите **Разрешить значение NULL**.  
  
6.  Нажмите кнопку **ОК**.  
  
7.  Чтобы выполнить отчет, перейдите на вкладку **Предварительный просмотр** . Обратите внимание на поле ввода параметров в верхней части отчета. Вы можете сделать одно из двух:  
  
    -   щелкнуть «Просмотр отчета», чтобы отобразить весь отчет без использования параметра;  
  
    -   отменить выбор параметра **NULL** и ввести номер заказа, например *so71949*, а затем щелкнуть **Просмотреть отчет** , чтобы просмотреть в отчете только один заказ.  
    ![ssrs_tutorial_datadriven_reportviewer_parameter](../reporting-services/media/ssrs-tutorial-datadriven-reportviewer-parameter.png) 
 
  
## <a name="bkmk_redeploy"></a>Повторное развертывание отчета  
  
1.  Повторно разверните отчет, с тем чтобы конфигурация подписки, которая будет создана на следующем занятии, могла использовать изменения, внесенные на этом занятии. Дополнительные сведения о свойствах проекта, использованных в учебнике по таблицам, см. в разделе "Публикация отчета на сервере отчетов (необязательно)" [занятия 6 "Добавление группирования и итогов" (службы Reporting Services)](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).  
  
2.  На панели инструментов щелкните **Построить** , а затем ― **Развернуть учебник**.  
  
## <a name="next-steps"></a>Следующие шаги  
+ Отчет успешно настроен для получения данных с применением сохраненных учетных данных. Данные можно фильтровать с помощью параметра. 
+ На следующем занятии вы настроите подписку с помощью страниц управляемой данными подписки на веб-портале. См. [Занятие 3. Определение управляемой данными подписки](../reporting-services/lesson-3-defining-a-data-driven-subscription.md).  
  
## <a name="see-also"></a>См. также:  
[Управление источниками данных отчета](../reporting-services/report-data/manage-report-data-sources.md)  
[Задание учетных данных и сведениях о соединении для источников данных отчета](../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
[Создание управляемой данными подписки (учебник по службам SSRS)](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md)  
[Создание простого табличного отчета (учебник по службам SSRS)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  
  
  
  

