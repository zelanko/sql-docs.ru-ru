---
title: Урок 2. Изменение свойств источника данных отчета | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: c962b0ff-ce8a-4742-8262-dc730901afcf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 41746f2938afd17e59dc4a9f2278179e4ccc1695
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59964800"
---
# <a name="lesson-2-modifying-the-report-data-source-properties"></a>Урок 2. Изменение свойств источника данных отчета
  На этом занятии с помощью диспетчера отчетов будет выбираться отчет, который необходимо доставить получателям. Управляемая данными подписка, которую вы создадите, будет распространять отчет **Заказ на продажу** , созданный при работе с учебником [Создание простого табличного отчета (учебник по службам SSRS)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md). В последующих шагах будут изменены сведения о соединении с источником данных, используемые в отчете для получения данных. Только отчеты, использующие **сохраненные учетные данные** для доступа к источнику данных для отчета, могут распространяться с помощью управляемой данными подписки. Сохраненные учетные данные нужны для автоматической обработки отчета.  
  
 Вы также измените набор данных и отчет, включив в них параметр для фильтрации отчета по `[Order]` , с тем чтобы подписка могла выдавать разные экземпляры отчета для определенных заказов и форматов подготовки к просмотру.  
  
 **В этом разделе:**  
  
-   [Изменение свойств источника данных](#bkmk_modify_datasource)  
  
-   [Для изменения набора данных AdventureWorksDataset](#bkmk_modify_dataset)  
  
-   [Добавление параметра отчета и повторная публикация отчета](#bkmk_add_reportparameter)  
  
-   [Повторное развертывание отчета](#bkmk_redeploy)  
  
##  <a name="bkmk_modify_datasource"></a> Изменение свойств источника данных  
  
1.  Запуск [диспетчера отчетов &#40;собственный режим служб SSRS&#41; ](../../2014/reporting-services/report-manager-ssrs-native-mode.md) с правами администратора, например, щелкните правой кнопкой мыши значок для Internet Explorer и нажмите кнопку **Запуск от имени администратора**.  
  
2.  Перейдите в папку с отчетом **Sales Orders** и в контекстном меню отчета щелкните пункт **Управление**.  
  
     ![Откройте контекстное меню отчета и выбор управления](../../2014/tutorials/media/ssrs-tutorial-datadriven-manage-report.gif "откройте контекстное меню отчета и выбор управления")  
  
3.  Перейдите на вкладку **Источники данных** .  
  
4.  В поле **Тип соединения**укажите **Microsoft SQL Server**.  
  
5.  Будет использоваться следующая строка подключения к пользовательскому источнику данных (предполагается, что образец базы данных находится на локальном сервере баз данных):  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2012  
    ```  
  
6.  Щелкните **Учетные данные, которые безопасно хранятся на сервере отчетов**.  
  
7.  Введите имя пользователя (в виде *домен\имя*) и пароль. Воспользуйтесь именем входа, у которого есть разрешение на доступ к базе данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] .  
  
8.  Установите флажок **Использовать учетные данные Windows при соединение с источником данных**и нажмите кнопку **ОК**. Если учетная запись домена не используется (например, используется учетная запись [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ), не устанавливайте этот флажок.  
  
9. Нажмите кнопку **Проверить соединение** , чтобы проверить соединение с источником данных.  
  
10. Нажмите кнопку **Применить**.  
  
11. Просмотрите отчет, чтобы убедиться, что он выполняется с указанными учетными данными. Чтобы просмотреть отчет, щелкните вкладку **Просмотр** . Обратите внимание, что если отчет уже открыт, необходимо выбрать имя сотрудника и затем нажать кнопку **Просмотреть отчет** , чтобы просмотреть этот отчет.  
  
##  <a name="bkmk_modify_dataset"></a> Для изменения набора данных AdventureWorksDataset  
  
1.  Откройте отчет Sales Orders в среде [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]  
  
2.  Щелкните правой кнопкой мыши набор данных `AdventureWorksDataset` и выберите пункт **Свойства набора данных**.  
  
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
  
##  <a name="bkmk_add_reportparameter"></a> Добавление параметра отчета и повторная публикация отчета  
  
1.  В области **Данные отчета** нажмите кнопку **Создать** и выберите **Параметр...**.  
  
2.  В поле **Имя**введите `OrderNumber`.  
  
3.  В поле **Подсказка**введите `OrderNumber`.  
  
4.  Выберите **Разрешить пустое значение ("")**.  
  
5.  Выберите **Разрешить значение NULL**.  
  
6.  Нажмите кнопку **ОК**. Параметр будет добавлен в область **Данные отчета** и будет выглядеть, как на следующем изображении:  
  
     ![В области данных отчета добавлен новый параметр](../../2014/tutorials/media/ssrs-tutorial-datadriven-parameter.gif "новый параметр добавлен в область данных отчета")  
  
7.  Перейдите на вкладку **Просмотр** , чтобы запустить отчет. Обратите внимание на поле ввода параметра вверху отчета. Вы можете сделать одно из двух:  
  
    -   щелкнуть «Просмотр отчета», чтобы отобразить весь отчет без использования параметра;  
  
    -   снять выбор параметра NULL и ввести номер заказа, например so71949, чтобы просмотреть в отчете только один заказ.  
  
         ![Средство просмотра отчетов с отображаемой областью параметров](../../2014/tutorials/media/ssrs-tutorial-datadriven-reportviewer-parameter.gif "средство просмотра отчетов с отображаемой областью параметров")  
  
8.  Повторно разверните отчет, с тем чтобы конфигурация подписки, которая будет создана на следующем занятии, могла использовать изменения, внесенные на этом занятии. Дополнительные сведения о свойствах проекта, использованных в учебнике по таблицам, см. в разделе «Публикация отчета на сервере отчетов (необязательно)» из [Lesson 6: Добавление группирования и итогов (службы Reporting Services)](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).  
  
##  <a name="bkmk_redeploy"></a> Повторное развертывание отчета  
  
1.  Повторно разверните отчет, с тем чтобы конфигурация подписки, которая будет создана на следующем занятии, могла использовать изменения, внесенные на этом занятии. Дополнительные сведения о свойствах проекта, использованных в учебнике по таблицам, см. в разделе «Публикация отчета на сервере отчетов (необязательно)» из [Lesson 6: Добавление группирования и итогов (службы Reporting Services)](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).  
  
2.  На панели инструментов щелкните **Построить** , а затем ― **Развернуть учебник**.  
  
## <a name="next-steps"></a>Следующие шаги  
 Отчет настроен для получения данных с применением сохраненных учетных данных. Далее предстоит определить подписку с помощью страниц управляемых данными подписок в диспетчере отчетов. См. [Занятие 3. Определение управляемой данными подписки](../reporting-services/lesson-3-defining-a-data-driven-subscription.md).  
  
## <a name="see-also"></a>См. также  
 [Управление источниками данных отчета](report-data/manage-report-data-sources.md)   
 [Задание учетных данных и сведениях о соединении для источников данных отчета](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Создание управляемой данными подписки (учебник по службам SSRS)](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md)   
 [Создание простого табличного отчета (учебник по службам SSRS)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  
  
  
