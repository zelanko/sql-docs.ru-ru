---
title: Занятие 8. Создание фильтра данных | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 19ccbdba-e3da-40a4-b652-32c628cf32e5
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: cdc62c2e2fa4b4a6bfd662c1b20de6287fc8ff86
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278840"
---
# <a name="lesson-8-create-a-data-filter"></a>Занятие 8. Создание фильтра данных
  После добавления к родительскому отчету операции детализации следующий шаг состоит в создании фильтра данных для таблицы данных, которая определена в дочернем отчете.  
  
 Для детализированного отчета можно создать фильтр на основе таблицы **или** фильтр запроса. На этом занятии приведены указания по обоим вариантам.  
  
## <a name="table-based-filter"></a>Фильтр на основе таблицы  
 Для реализации фильтра на основе таблицы необходимо выполнить следующие задачи.  
  
-   Добавить критерий фильтра к табликсу в дочернем отчете.  
  
-   Создать функцию, которая выбирает нефильтрованные данные из таблицы `PurchaseOrderDetail`.  
  
-   Добавить обработчик событий, который связывает таблицу данных `PurchaseOrderDetail` с дочерним отчетом.  
  
#### <a name="to-add-a-filter-expression-to-the-tablix-in-the-child-report"></a>Добавление критерия фильтра к табликсу в дочернем отчете  
  
1.  Откройте дочерний отчет.  
  
2.  Выберите заголовок столбца в табликсе, щелкните правой кнопкой мыши выделенную серым цветом ячейку, которая отображается над заголовком столбца и нажмите кнопку **свойства Табликса**.  
  
3.  Щелкните **фильтры** странице, а затем выберите **добавить**.  
  
4.  В **выражение** выберите `ProductID` из раскрывающегося списка. Это столбец, к которому применяется фильтр.  
  
5.  Нажмите кнопку равенства (**=**) оператор в **оператор** стрелку раскрывающегося списка.  
  
6.  Нажмите кнопку выражения рядом с полем **значение** щелкните **параметры** в **категории** области, а затем дважды щелкните пункт `productid` в  **Значения** области. Поле **Задать выражение для: Значение** теперь должно содержать выражение, аналогичное **=Parameters!productid.Value**.  
  
7.  Нажмите кнопку **"ОК",** и **ОК** через **свойства Табликса** диалоговое окно.  
  
8.  Сохраните RDLC-файл.  
  
#### <a name="to-create-a-function-that-selects-unfiltered-data-from-the-purchaseordedetail-table"></a>Создание функции, которая выбирает нефильтрованные данные из таблицы PurchaseOrdeDetail  
  
1.  В обозревателе решений разверните Default.aspx, затем дважды щелкните Default.aspx.cs.  
  
2.  Создайте новую функцию, которая принимает параметр `productid` типа Integer, возвращает объект `datatable` и выполняет следующие действия.  
  
    1.  Создает экземпляр набора данных, `DataSet2`, который был создан на шаге 2 [занятия 4: определение подключения к данным и таблицы данных для дочернего отчета](lesson-4-define-a-data-connection-and-data-table-for-child-report.md).  
  
    2.  Создает подключение к базе данных SqlServer для выполнения запроса, который был определен на **занятии 4. "Определение подключения к данным и таблицы данных для дочернего отчета"**.  
  
    3.  Запрос возвратит нефильтрованные данные.  
  
    4.  Заполнение экземпляра набора данных нефильтрованными данными путем выполнения запроса.  
  
    5.  Возврат таблицы данных `PurchaseOrderDetail`.  
  
         Функция будет иметь примерно такой вид, как показано ниже. (Этот пример приведен только для справки. Для выборки необходимых данных для дочернего отчета можно применять любой подход.)  
  
        ```  
        /// <summary>  
            /// Function to query PurchaseOrderDetail table, fetch the  
            /// unfiltered data and bind it with the Child report  
            /// </summary>  
            /// <returns>A dataTable of type PurchaseOrderDetail</returns>  
            private DataTable GetPurchaseOrderDetail()  
            {  
                try  
                {  
                    //Create the instance for the typed dataset, DataSet2 which will   
                    //hold the [PurchaseOrderDetail] table details.  
                    //The dataset was created as part of the tutorial in Step 4.  
                    DataSet2 ds = new DataSet2();  
  
                    //Create a SQL Connection to the AdventureWorks2008 database using Windows Authentication.  
                    using (SqlConnection sqlconn = new SqlConnection("Data Source=.;Initial Catalog=Adventureworks;Integrated Security=SSPI"))  
                    {  
                        //Building the dynamic query with the parameter ProductID.  
                        SqlDataAdapter adap = new SqlDataAdapter("SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail ", sqlconn);  
                        //Executing the QUERY and fill the dataset with the PurchaseOrderDetail table data.  
                        adap.Fill(ds, "PurchaseOrderDetail");  
                    }  
  
                    //Return the PurchaseOrderDetail table for the Report Data Source.  
                    return ds.PurchaseOrderDetail;  
                }  
                catch  
                {  
                    throw;  
                }  
            }  
        ```  
  
#### <a name="to-add-an-event-handler-that-binds-the-purchaseorderdetail-datatable-to-the-child-report"></a>Добавление обработчика событий, который связывает таблицу данных PurchaseOrderDetail с дочерним отчетом  
  
1.  Откройте страницу Default.aspx.  
  
2.  Щелкните правой кнопкой мыши элемент управления ReportViewer, а затем нажмите кнопку **свойства.**  
  
3.  На **свойства** щелкните **события** значок.  
  
4.  Дважды щелкните **детализации** событий.  
  
     Это приведет к добавлению раздела обработчика событий в код, который выглядит так, как в приведенном ниже блоке.  
  
    ```  
    protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
    {  
    }  
    ```  
  
5.  Завершите подготовку обработчика событий. Он должен включать следующие функции.  
  
    1.  Выборка ссылки на объект дочернего отчета из параметра *DrillthroughEventArgs* .  
  
    2.  Вызов функции `GetPurchaseOrderDetail`  
  
    3.  Привязка таблицы данных `PurchaseOrderDetail` к соответствующему источнику данных отчета.  
  
         Код обработчика событий в законченном виде будет выглядеть следующим образом.  
  
        ```  
        protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
            {  
                try  
                {  
                     //Get the instance of the Target report, in our case the JumpReport.rdlc.  
                    LocalReport report = (LocalReport)e.Report;  
  
                     //Binding the DataTable to the Child report dataset.  
                    //The name DataSet1 which can be located from,   
                    //Go to Design view of Child.rdlc, Click View menu -> Report Data  
                    //You'll see this name under DataSet2.  
                    report.DataSources.Add(new ReportDataSource("DataSet1", GetPurchaseOrderDetail()));  
                }  
                catch (Exception ex)  
                {  
                    Response.Write(ex.Message);  
                }  
            }  
        ```  
  
6.  Сохраните файл.  
  
## <a name="query-filter"></a>Фильтр с запросом  
 Для реализации фильтра с запросом необходимо выполнить следующие задачи.  
  
-   Создание функции, которая выбирает фильтрованные данные из таблицы `PurchaseOrderDetail`.  
  
-   Добавление обработчика событий, который получает значения параметров и привязывает таблицу данных `PurchaseOrdeDetail` к дочернему отчету.  
  
#### <a name="to-create-a-function-that-selects-filtered-data-from-the-purchaseorderdetail-table"></a>Создание функции, которая выбирает фильтрованные данные из таблицы PurchaseOrderDetail  
  
1.  В обозревателе решений разверните Default.aspx, затем дважды щелкните Default.aspx.cs.  
  
2.  Создайте новую функцию, которая принимает параметр `productid` типа Integer, возвращает объект `datatable` и выполняет следующие действия.  
  
    1.  Создает экземпляр набора данных, `DataSet2`, который был создан на шаге 2 [занятия 4: определение подключения к данным и таблицы данных для дочернего отчета](lesson-4-define-a-data-connection-and-data-table-for-child-report.md).  
  
    2.  Создает подключение к базе данных SqlServer для выполнения запроса, который был определен на **занятии 4. "Определение подключения к данным и таблицы данных для дочернего отчета"**.  
  
    3.  Запрос должен включать параметр `productid` для обеспечения фильтрации возвращаемых данных с учетом значения `ProductID`, выбранного в родительском отчете.  
  
    4.  Заполнение экземпляра набора данных фильтрованными данными путем выполнения запроса.  
  
    5.  Возврат таблицы данных `PurchaseOrderDetail`.  
  
         Функция будет иметь примерно такой вид, как показано ниже. (Этот пример приведен только для справки. Для выборки необходимых данных для дочернего отчета можно применять любой подход.)  
  
        ```  
        /// <summary>  
            /// Function to query PurchaseOrderDetail table and filter the  
            /// data for a specific ProductID selected in the Parent report.  
            /// </summary>  
            /// <param name="productid">Parameter passed from the Parent report to filter data.</param>  
            /// <returns>A dataTable of type PurchaseOrderDetail</returns>  
            private DataTable GetPurchaseOrderDetail(int productid)  
            {  
                try  
                {  
                    //Create the instance for the typed dataset, DataSet2 which will   
                    //hold the [PurchaseOrderDetail] table details.  
                    //The dataset was created as part of the tutorial in Step 4.  
                    DataSet2 ds = new DataSet2();  
  
                    //Create a SQL Connection to the AdventureWorks2008 database using Windows Authentication.  
                    using (SqlConnection sqlconn = new SqlConnection("Data Source=.;Initial Catalog=Adventureworks;Integrated Security=SSPI"))  
                    {  
                        //Building the dynamic query with the parameter ProductID.  
                        SqlDataAdapter adap = new SqlDataAdapter("SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail where ProductID = " + productid, sqlconn);  
                        //Executing the QUERY and fill the dataset with the PurchaseOrderDetail table data.  
                        adap.Fill(ds, "PurchaseOrderDetail");  
                    }  
  
                    //Return the PurchaseOrderDetail table for the Report Data Source.  
                    return ds.PurchaseOrderDetail;  
                }  
                catch  
                {  
                    throw;  
                }  
            }  
        ```  
  
#### <a name="to-add-an-event-handler-that-retrieves-parameter-values-and-binds-the-purchaseordedetail-datatable-to-the-child-report"></a>Добавление обработчика событий, который получает значения параметров и связывает таблицу данных PurchaseOrdeDetail с дочерним отчетом  
  
1.  Откройте страницу Default.aspx.  
  
2.  Щелкните правой кнопкой мыши элемент управления ReportViewer, а затем нажмите кнопку **свойства**.  
  
3.  На **свойства** панели щелкните **события** значок.  
  
4.  Дважды щелкните **детализации** событий.  
  
     Это приведет к добавлению раздела с обработчиком событий в код, который будет выглядеть примерно так.  
  
    ```  
    protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
    {  
    }  
    ```  
  
5.  Завершите подготовку обработчика событий. Он должен выполнять следующие функции.  
  
    1.  Выборка ссылки на объект дочернего отчета из параметра *DrillthroughEventArgs* .  
  
    2.  Получение списка параметров дочернего отчета из имеющегося объекта дочернего отчета.  
  
    3.  Итерация в коллекции параметров и выборка значения для параметра `ProductID`, переданного из родительского отчета.  
  
    4.  Вызов функции `GetPurchaseOrderDetail` и передача значения для параметра `ProductID`.  
  
    5.  Привязка таблицы данных `PurchaseOrderDetail` к соответствующему источнику данных отчета.  
  
         Код обработчика событий в законченном виде будет выглядеть следующим образом.  
  
        ```  
        protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
            {  
                try  
                {  
                    //Variable to store the parameter value passed from the MainReport.  
                    int productid = 0;  
  
                    //Get the instance of the Target report, in our case the JumpReport.rdlc.  
                    LocalReport report = (LocalReport)e.Report;  
  
                    //Get all the parameters passed from the main report to the target report.  
                    //OriginalParametersToDrillthrough actually returns a Generic list of   
                    //type ReportParameter.  
                    IList<ReportParameter> list = report.OriginalParametersToDrillthrough;  
  
                    //Parse through each parameters to fetch the values passed along with them.  
                    foreach (ReportParameter param in list)  
                    {  
                        //Since we know the report has only one parameter and it is not a multivalued,   
                        //we can directly fetch the first value from the Values array.  
                        productid = Convert.ToInt32(param.Values[0].ToString());  
                    }  
  
                    //Binding the DataTable to the Child report dataset.  
                    //The name DataSet1 which can be located from,   
                    //Go to Design view of Child.rdlc, Click View menu -> Report Data  
                    //You'll see this name under DataSet2.  
                    report.DataSources.Add(new ReportDataSource("DataSet1", GetPurchaseOrderDetail(productid)));  
                }  
                catch (Exception ex)  
                {  
                    Response.Write(ex.Message);  
                }  
            }  
        ```  
  
6.  Сохраните файл.  
  
## <a name="next-task"></a>Следующая задача  
 Тем самым был успешно создан фильтр данных для таблицы данных, которая определена в дочернем отчете. Затем необходимо построить и запустить приложение веб-сайта.  
  
  
