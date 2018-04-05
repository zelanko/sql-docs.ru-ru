---
title: Использование элемента управления WinForms ReportViewer | Документы Майкрософт
ms.custom: ''
ms.date: 09/06/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: ''
ms.component: application-integration
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ReportViewer controls
ms.assetid: 29fb9f7d-ba65-49fd-9cbc-4c380869de96
caps.latest.revision: 28
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Active
ms.openlocfilehash: 70933dbcd48c06d74879845679d817b9890a926b
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="using-the-winforms-reportviewer-control"></a>Использование элемента управления WinForms ReportViewer
  Для просмотра отчетов, развернутых на сервере отчетов, и отчетов, существующих в локальной файловой системе, можно использовать элемент управления WinForms ReportViewer для подготовки отчетов к просмотру в приложении Windows.  
  
## <a name="to-add-the-reportviewer-control-to-a-windows-application"></a>Добавление элемента управления ReportViewer в приложение Windows  
  
1.  Создайте новое приложение Windows с помощью [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] или [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].  
  
     \- - или -  
  
     Открыть существующий проект приложения Windows и добавить новую форму.  
  
2.  Укажите элемент управления ReportViewer в окне **Панель элементов**. Если окно **Панель элементов** не отображается, к нему можно получить доступ из меню **Вид**, выбрав пункт **Панель элементов**.  
  
     ![Выбор элемента управления ReportViewer](../../reporting-services/application-integration/media/windowsapp-toolboxreportviewer.png "Выбор элемента управления ReportViewer")  
  
3.  Перетащите элемент управления ReportViewer в область конструктора Windows Form.  
  
     В форму будет добавлен элемент управления ReportViewer с именем reportViewer1.  
  
 После добавления элемента управления в форму появляется смарт-тег **Задачи ReportViewer** и выводится приглашение выбрать отчет.  
  
 Если требуемый отчет развернут на сервере отчетов, выберите параметр **\<Отчет по серверу>** из раскрывающегося списка **Выбор отчета**. После выбора параметра **\<Отчет по серверу>** на экране появляются два свойства : **URL-адрес сервера отчетов** и **Путь к отчету**. Свойство **URL-адрес сервера отчетов** задает адрес сервера отчетов, а свойство **Путь к отчету** задает полный путь к подготавливаемому к просмотру отчету.  
  
 ![Выбор отчета сервера](../../reporting-services/application-integration/media/windowsapp-serverreportsettings.png "Выбор отчета сервера")  
  
 Если просматриваемый отчет является отчетом в локальном режиме, выберите параметр **Создать новый отчет** для запуска конструктора отчетов или отчет, который уже является частью существующего проекта.  
  
 ![Выбор локального отчета](../../reporting-services/application-integration/media/windowsapp-localreportsettings.png "Выбор локального отчета")  
  
## <a name="viewing-reports-in-remote-processing-mode"></a>Просмотр отчетов в режиме удаленной обработки  
 В следующем примере показана подготовка к просмотру отчета, развернутого на сервере отчетов при помощи элемента управления WinForms ReportViewer. В этом примере используется отчет Sales Order Detail, который включен в проект с образцами отчетов [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
 
**C#**
```csharp  
public partial class Form1 : Form  
{  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        // Set the processing mode for the ReportViewer to Remote  
        reportViewer1.ProcessingMode = ProcessingMode.Remote;  
  
        ServerReport serverReport = reportViewer1.ServerReport;  
  
        // Get a reference to the default credentials  
        System.Net.ICredentials credentials =  
            System.Net.CredentialCache.DefaultCredentials;  
  
        // Get a reference to the report server credentials  
        ReportServerCredentials rsCredentials =  
            serverReport.ReportServerCredentials;  
  
        // Set the credentials for the server report  
        rsCredentials.NetworkCredentials = credentials;  
  
        // Set the report server URL and report path  
        serverReport.ReportServerUrl =   
            new Uri("http:// <Server Name>/reportserver");  
        serverReport.ReportPath =   
            "/AdventureWorks Sample Reports/Sales Order Detail";  
  
        // Create the sales order number report parameter  
        ReportParameter salesOrderNumber = new ReportParameter();  
        salesOrderNumber.Name = "SalesOrderNumber";  
        salesOrderNumber.Values.Add("SO43661");  
  
        // Set the report parameters for the report  
        reportViewer1.ServerReport.SetParameters(  
            new ReportParameter[] { salesOrderNumber });  
  
        // Refresh the report  
        reportViewer1.RefreshReport();  
    }  
}  
```  
**VB.NET**
```vb  
Imports Microsoft.Reporting.WinForms  
  
Public Class Form1  
  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
                           ByVal e As System.EventArgs) _  
                           Handles MyBase.Load  
  
        'Set the processing mode for the ReportViewer to Remote  
        reportViewer1.ProcessingMode = ProcessingMode.Remote  
  
        Dim serverReport As ServerReport  
        serverReport = reportViewer1.ServerReport  
  
        'Get a reference to the default credentials  
        Dim credentials As System.Net.ICredentials  
        credentials = System.Net.CredentialCache.DefaultCredentials  
  
        'Get a reference to the report server credentials  
        Dim rsCredentials As ReportServerCredentials  
        rsCredentials = serverReport.ReportServerCredentials  
  
        'Set the credentials for the server report  
        rsCredentials.NetworkCredentials = credentials  
  
        'Set the report server URL and report path  
        serverReport.ReportServerUrl = _  
           New Uri("http://<Server Name>/reportserver")  
        serverReport.ReportPath = _  
           "/AdventureWorks Sample Reports/Sales Order Detail"  
  
        'Create the sales order number report parameter  
        Dim salesOrderNumber As New ReportParameter()  
        salesOrderNumber.Name = "SalesOrderNumber"  
        salesOrderNumber.Values.Add("SO43661")  
  
        'Set the report parameters for the report  
        Dim parameters() As ReportParameter = {salesOrderNumber}  
        serverReport.SetParameters(parameters)  
  
        'Refresh the report  
        reportViewer1.RefreshReport()  
    End Sub  
  
End Class  
```  
  
## <a name="viewing-reports-in-local-processing-mode"></a>Просмотр отчетов в режиме локальной обработки  
 В следующем примере показана подготовка к просмотру отчета, который является частью приложения Windows и не был помещен на сервер отчетов.  
  
### <a name="to-add-the-sales-order-detail-report-to-a-windows-application"></a>Добавление отчета «Сведения о заказе на продажу» в приложение Windows  
  
1.  Открыть проект Windows, в который будет добавлен отчет.  
  
2.  В меню **Проект** выберите пункт **Добавить существующий элемент**.  
  
3.  Перейти в папку, в которой были установлены проекты образцов отчетов [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
     Чтобы скачать примеры отчетов, перейдите в раздел [Примеры отчетов AdventureWorks 2012](http://go.microsoft.com/fwlink/?LinkId=404153).  
  
4.  Выберите файл Sales Order Detail.rdl и нажмите кнопку **Добавить**.  
  
     Файл «Сведения о заказе на продажу.rdl» теперь станет частью проекта.  
  
     ![Отчет со сведениями о заказах на продажу](../../reporting-services/application-integration/media/windowsapp-salesorderdetailreport.png "Отчет со сведениями о заказах на продажу")  
  
5.  Щелкните правой кнопкой мыши файл Sales Order Detail.rdl в обозревателе решений и выберите команду **Переименовать**. Переименуйте отчет в **Сведения о заказах на продажу.rdlc** и нажмите клавишу ВВОД.  
  
     Если обозреватель решений не отображается, его можно открыть из меню **Вид**, выбрав пункт **Обозреватель решений**.  
  
    > [!NOTE]  
    >  Переименование расширения из rdl в rdlc позволит редактировать отчет при помощи конструктора отчетов для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)].  
  
6.  После переименования отчета выберите файл и перейдите в окно «Свойства». Для свойства **Копировать в выходной каталог** задайте значение **Копировать более новые**.  
  
     ![Настройка параметра "Копировать в выходной каталог"](../../reporting-services/application-integration/media/windowsapp-copytooutputsetting.png "Настройка параметра "Копировать в выходной каталог"")  
  
     Если окно **Свойства** не отображается, можно открыть его из меню **Вид**, выбрав **Окно "Свойства"**.  
  
 В следующем примере кода создается набор данных для данных о заказе на продажу, а затем подготавливается к просмотру отчет «Сведения о заказе на продажу» в локальном режиме.  

**C#**
```csharp  
public partial class Form1 : Form  
{  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        // Set the processing mode for the ReportViewer to Local  
        reportViewer1.ProcessingMode = ProcessingMode.Local;  
  
        LocalReport localReport = reportViewer1.LocalReport;  
  
        localReport.ReportPath = "Sales Order Detail.rdlc";  
  
        DataSet dataset = new DataSet("Sales Order Detail");  
  
        string salesOrderNumber = "SO43661";  
  
        // Get the sales order data  
        GetSalesOrderData(salesOrderNumber, ref dataset);  
  
        // Create a report data source for the sales order data  
        ReportDataSource dsSalesOrder = new ReportDataSource();  
        dsSalesOrder.Name = "SalesOrder";  
        dsSalesOrder.Value = dataset.Tables["SalesOrder"];  
  
        localReport.DataSources.Add(dsSalesOrder);  
  
        // Get the sales order detail data  
        GetSalesOrderDetailData(salesOrderNumber, ref dataset);  
  
        // Create a report data source for the sales order detail   
        // data  
        ReportDataSource dsSalesOrderDetail =  
            new ReportDataSource();  
        dsSalesOrderDetail.Name = "SalesOrderDetail";  
        dsSalesOrderDetail.Value =  
            dataset.Tables["SalesOrderDetail"];  
  
        localReport.DataSources.Add(dsSalesOrderDetail);  
  
        // Create a report parameter for the sales order number   
        ReportParameter rpSalesOrderNumber = new ReportParameter();  
        rpSalesOrderNumber.Name = "SalesOrderNumber";  
        rpSalesOrderNumber.Values.Add("SO43661");  
  
        // Set the report parameters for the report  
        localReport.SetParameters(  
            new ReportParameter[] { rpSalesOrderNumber });  
  
        // Refresh the report  
        reportViewer1.RefreshReport();  
    }  
  
    private void GetSalesOrderData(string salesOrderNumber,  
                                   ref DataSet dsSalesOrder)  
    {  
        string sqlSalesOrder =  
            "SELECT SOH.SalesOrderNumber, S.Name AS Store, " +  
            "       SOH.OrderDate, C.FirstName AS SalesFirstName, " +  
            "       C.LastName AS SalesLastName, E.Title AS " +  
            "       SalesTitle, SOH.PurchaseOrderNumber, " +  
            "       SM.Name AS ShipMethod, BA.AddressLine1 " +  
            "       AS BillAddress1, BA.AddressLine2 AS " +  
            "       BillAddress2, BA.City AS BillCity, " +  
            "       BA.PostalCode AS BillPostalCode, BSP.Name " +  
            "       AS BillStateProvince, BCR.Name AS " +  
            "       BillCountryRegion, SA.AddressLine1 AS " +  
            "       ShipAddress1, SA.AddressLine2 AS " +  
            "       ShipAddress2, SA.City AS ShipCity, " +  
            "       SA.PostalCode AS ShipPostalCode, SSP.Name " +  
            "       AS ShipStateProvince, SCR.Name AS " +  
            "       ShipCountryRegion, CC.Phone AS CustPhone, " +  
            "       CC.FirstName AS CustFirstName, CC.LastName " +  
            "       AS CustLastName " +  
            "FROM   Person.Address SA INNER JOIN " +  
            "       Person.StateProvince SSP ON " +  
            "       SA.StateProvinceID = SSP.StateProvinceID " +  
            "       INNER JOIN Person.CountryRegion SCR ON " +  
            "       SSP.CountryRegionCode = SCR.CountryRegionCode " +  
            "       RIGHT OUTER JOIN Sales.SalesOrderHeader SOH " +  
            "       LEFT OUTER JOIN  Person.Contact CC ON " +  
            "       SOH.ContactID = CC.ContactID LEFT OUTER JOIN" +  
            "       Person.Address BA INNER JOIN " +  
            "       Person.StateProvince BSP ON " +  
            "       BA.StateProvinceID = BSP.StateProvinceID " +  
            "       INNER JOIN Person.CountryRegion BCR ON " +  
            "       BSP.CountryRegionCode = " +  
            "       BCR.CountryRegionCode ON SOH.BillToAddressID " +  
            "       = BA.AddressID ON  SA.AddressID = " +  
            "       SOH.ShipToAddressID LEFT OUTER JOIN " +  
            "       Person.Contact C RIGHT OUTER JOIN " +  
            "       HumanResources.Employee E ON C.ContactID = " +  
            "       E.ContactID ON SOH.SalesPersonID = " +  
            "       E.EmployeeID LEFT OUTER JOIN " +  
            "       Purchasing.ShipMethod SM ON SOH.ShipMethodID " +  
            "       = SM.ShipMethodID LEFT OUTER JOIN Sales.Store" +  
            "        S ON SOH.CustomerID = S.CustomerID " +  
            "WHERE  (SOH.SalesOrderNumber = @SalesOrderNumber)";  
  
        SqlConnection connection = new  
            SqlConnection("Data Source=(local); " +  
                          "Initial Catalog=AdventureWorks; " +  
                          "Integrated Security=SSPI");  
  
        SqlCommand command =  
            new SqlCommand(sqlSalesOrder, connection);  
  
        command.Parameters.Add(  
            new SqlParameter("SalesOrderNumber",  
            salesOrderNumber));  
  
        SqlDataAdapter salesOrderAdapter = new  
            SqlDataAdapter(command);  
  
        salesOrderAdapter.Fill(dsSalesOrder, "SalesOrder");  
    }  
  
    private void GetSalesOrderDetailData(string salesOrderNumber,  
                           ref DataSet dsSalesOrder)  
    {  
        string sqlSalesOrderDetail =  
            "SELECT  SOD.SalesOrderDetailID, SOD.OrderQty, " +  
            "        SOD.UnitPrice, CASE WHEN " +  
            "        SOD.UnitPriceDiscount IS NULL THEN 0 " +  
            "        ELSE SOD.UnitPriceDiscount END AS " +  
            "        UnitPriceDiscount, SOD.LineTotal, " +  
            "        SOD.CarrierTrackingNumber, " +  
            "        SOD.SalesOrderID, P.Name, P.ProductNumber " +  
            "FROM    Sales.SalesOrderDetail SOD INNER JOIN " +  
            "        Production.Product P ON SOD.ProductID = " +  
            "        P.ProductID INNER JOIN " +  
            "        Sales.SalesOrderHeader SOH ON " +  
            "        SOD.SalesOrderID = SOH.SalesOrderID " +  
            "WHERE   (SOH.SalesOrderNumber = @SalesOrderNumber) " +  
            "ORDER BY SOD.SalesOrderDetailID";  
  
        using (SqlConnection connection = new  
            SqlConnection("Data Source=(local); " +  
                          "Initial Catalog=AdventureWorks; " +  
                          "Integrated Security=SSPI"))  
        {  
  
            SqlCommand command =  
                new SqlCommand(sqlSalesOrderDetail, connection);  
  
            command.Parameters.Add(  
                new SqlParameter("SalesOrderNumber",  
                salesOrderNumber));  
  
            SqlDataAdapter salesOrderDetailAdapter = new  
                SqlDataAdapter(command);  
  
            salesOrderDetailAdapter.Fill(dsSalesOrder,  
                "SalesOrderDetail");  
        }  
    }  
}  
```  
**VB.NET**
```vb  
Imports System.Data.SqlClient  
Imports Microsoft.Reporting.WinForms  
  
Public Class Form1  
  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
                        ByVal e As System.EventArgs) _  
                        Handles MyBase.Load  
  
        'Set the processing mode for the ReportViewer to Local  
        reportViewer1.ProcessingMode = ProcessingMode.Local  
  
        Dim localReport As LocalReport  
        localReport = reportViewer1.LocalReport  
  
        localReport.ReportEmbeddedResource = _  
            "ReportViewerIntro.Sales Order Detail.rdlc"  
  
        Dim dataset As New DataSet("Sales Order Detail")  
  
        Dim salesOrderNumber As String = "SO43661"  
  
        'Get the sales order data  
        GetSalesOrderData(salesOrderNumber, dataset)  
  
        'Create a report data source for the sales order data  
        Dim dsSalesOrder As New ReportDataSource()  
        dsSalesOrder.Name = "SalesOrder"  
        dsSalesOrder.Value = dataset.Tables("SalesOrder")  
  
        localReport.DataSources.Add(dsSalesOrder)  
  
        'Get the sales order detail data  
        GetSalesOrderDetailData(salesOrderNumber, dataset)  
  
        'Create a report data source for the sales   
        'order detail data  
        Dim dsSalesOrderDetail As New ReportDataSource()  
        dsSalesOrderDetail.Name = "SalesOrderDetail"  
        dsSalesOrderDetail.Value = _  
            dataset.Tables("SalesOrderDetail")  
  
        localReport.DataSources.Add(dsSalesOrderDetail)  
  
        'Create a report parameter for the sales order number   
        Dim rpSalesOrderNumber As New ReportParameter()  
        rpSalesOrderNumber.Name = "SalesOrderNumber"  
        rpSalesOrderNumber.Values.Add("SO43661")  
  
        'Set the report parameters for the report  
        Dim parameters() As ReportParameter = {rpSalesOrderNumber}  
        localReport.SetParameters(parameters)  
  
        'Refresh the report  
        reportViewer1.RefreshReport()  
  
    End Sub  
  
    Private Sub GetSalesOrderData(ByVal salesOrderNumber As String, _  
                               ByRef dsSalesOrder As DataSet)  
  
        Dim sqlSalesOrder As String = _  
            "SELECT SOH.SalesOrderNumber, S.Name AS Store, " & _  
            "       SOH.OrderDate, C.FirstName AS SalesFirstName, " & _  
            "       C.LastName AS SalesLastName, E.Title AS " & _  
            "       SalesTitle, SOH.PurchaseOrderNumber, " & _  
            "       SM.Name AS ShipMethod, BA.AddressLine1 " & _  
            "       AS BillAddress1, BA.AddressLine2 AS " & _  
            "       BillAddress2, BA.City AS BillCity, " & _  
            "       BA.PostalCode AS BillPostalCode, BSP.Name " & _  
            "       AS BillStateProvince, BCR.Name AS " & _  
            "       BillCountryRegion, SA.AddressLine1 AS " & _  
            "       ShipAddress1, SA.AddressLine2 AS " & _  
            "       ShipAddress2, SA.City AS ShipCity, " & _  
            "       SA.PostalCode AS ShipPostalCode, SSP.Name " & _  
            "       AS ShipStateProvince, SCR.Name AS " & _  
            "       ShipCountryRegion, CC.Phone AS CustPhone, " & _  
            "       CC.FirstName AS CustFirstName, CC.LastName " & _  
            "       AS CustLastName " & _  
            "FROM   Person.Address SA INNER JOIN " & _  
            "       Person.StateProvince SSP ON " & _  
            "       SA.StateProvinceID = SSP.StateProvinceID " & _  
            "       INNER JOIN Person.CountryRegion SCR ON " & _  
            "       SSP.CountryRegionCode = SCR.CountryRegionCode " & _  
            "       RIGHT OUTER JOIN Sales.SalesOrderHeader SOH " & _  
            "       LEFT OUTER JOIN  Person.Contact CC ON " & _  
            "       SOH.ContactID = CC.ContactID LEFT OUTER JOIN" & _  
            "       Person.Address BA INNER JOIN " & _  
            "       Person.StateProvince BSP ON " & _  
            "       BA.StateProvinceID = BSP.StateProvinceID " & _  
            "       INNER JOIN Person.CountryRegion BCR ON " & _  
            "       BSP.CountryRegionCode = " & _  
            "       BCR.CountryRegionCode ON SOH.BillToAddressID " & _  
            "       = BA.AddressID ON  SA.AddressID = " & _  
            "       SOH.ShipToAddressID LEFT OUTER JOIN " & _  
            "       Person.Contact C RIGHT OUTER JOIN " & _  
            "       HumanResources.Employee E ON C.ContactID = " & _  
            "       E.ContactID ON SOH.SalesPersonID = " & _  
            "       E.EmployeeID LEFT OUTER JOIN " & _  
            "       Purchasing.ShipMethod SM ON SOH.ShipMethodID " & _  
            "       = SM.ShipMethodID LEFT OUTER JOIN Sales.Store" & _  
            "        S ON SOH.CustomerID = S.CustomerID " & _  
            "WHERE  (SOH.SalesOrderNumber = @SalesOrderNumber)"  
  
        Using connection As New SqlConnection( _  
                      "Data Source=(local); " & _  
                      "Initial Catalog=AdventureWorks; " & _  
                      "Integrated Security=SSPI")  
  
            Dim command As New SqlCommand(sqlSalesOrder, connection)  
  
            Dim parameter As New SqlParameter("SalesOrderNumber", _  
                salesOrderNumber)  
            command.Parameters.Add(parameter)  
  
            Dim salesOrderAdapter As New SqlDataAdapter(command)  
  
            salesOrderAdapter.Fill(dsSalesOrder, "SalesOrder")  
  
        End Using  
  
    End Sub  
  
    Private Sub GetSalesOrderDetailData( _  
                           ByVal salesOrderNumber As String, _  
                           ByRef dsSalesOrder As DataSet)  
  
        Dim sqlSalesOrderDetail As String = _  
            "SELECT  SOD.SalesOrderDetailID, SOD.OrderQty, " & _  
            "        SOD.UnitPrice, CASE WHEN " & _  
            "        SOD.UnitPriceDiscount IS NULL THEN 0 " & _  
            "        ELSE SOD.UnitPriceDiscount END AS " & _  
            "        UnitPriceDiscount, SOD.LineTotal, " & _  
            "        SOD.CarrierTrackingNumber, " & _  
            "        SOD.SalesOrderID, P.Name, P.ProductNumber " & _  
            "FROM    Sales.SalesOrderDetail SOD INNER JOIN " & _  
            "        Production.Product P ON SOD.ProductID = " & _  
            "        P.ProductID INNER JOIN " & _  
            "        Sales.SalesOrderHeader SOH ON " & _  
            "        SOD.SalesOrderID = SOH.SalesOrderID " & _  
            "WHERE   (SOH.SalesOrderNumber = @SalesOrderNumber) " & _  
            "ORDER BY SOD.SalesOrderDetailID"  
  
        Using connection As New SqlConnection( _  
                      "Data Source=(local); " & _  
                      "Initial Catalog=AdventureWorks; " & _  
                      "Integrated Security=SSPI")  
  
            Dim command As New SqlCommand(sqlSalesOrderDetail, _  
                                          connection)  
  
            Dim parameter As New SqlParameter("SalesOrderNumber", _  
                salesOrderNumber)  
            command.Parameters.Add(parameter)  
  
            Dim salesOrderDetailAdapter As New SqlDataAdapter(command)  
  
            salesOrderDetailAdapter.Fill(dsSalesOrder, _  
                "SalesOrderDetail")  
  
        End Using  
  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a>См. также:  
 [Интеграция служб Reporting Services с помощью элементов управления ReportViewer](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
  
  
