---
title: "Представление соединения (табличное) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 4b410b16-d36e-4185-bb20-922e66e5e2b7
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2fa62e16d603bb9adfff2410d14d376f358273be
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="connection-representation-tabular"></a>Представление соединения (табличное)
  Объект соединения определяет источник данных, который заполняет табличную модель.  
  
## <a name="connection-representation"></a>Представление соединения  
 Спецификация для объекта соединения соответствует правилам поставщиков OLE DB.  
  
### <a name="connection-in-amo"></a>Соединение в объектах AMO  
 Если для управления табличным шаблоном базы данных используются объекты AMO, то объект <xref:Microsoft.AnalysisServices.DataSource> из AMO соответствует «один к одному» логическому объекту соединения.  
  
 В следующем фрагменте кода показано, как создать источник данных объектов AMO или объект соединения в табличной модели.  
  
```  
  
//Create an OLEDB connection string  
StringBuilder SqlCnxStr = new StringBuilder();  
SqlCnxStr.Append(String.Format("Data Source={0};" ,SQLServer.Text));  
SqlCnxStr.Append(String.Format("Initial Catalog={0};", SQLDatabase.Text));  
SqlCnxStr.Append(String.Format("Persist Security Info={0};", false));  
SqlCnxStr.Append(String.Format("Integrated Security={0};", "SSPI"));  
SqlCnxStr.Append(String.Format("Provider={0}", "SQLNCLI11"));  
String DatasourceCnxString = SqlCnxStr.ToString();  
  
//Verify connection string and connectivity  
System.Data.OleDb.OleDbConnection OleDbCnx = new System.Data.OleDb.OleDbConnection(DatasourceCnxString);  
try  
{  
    OleDbCnx.Open();  
}  
catch ()  
{  
    throw;  
}  
String newDataSourceName = (string.IsNullOrEmpty(DataSourceName.Text) || string.IsNullOrWhiteSpace(DataSourceName.Text)) ? SQLDatabase.Text : DataSourceName.Text;  
AMO.DataSource newDatasource = newDatabase.DataSources.Add(newDataSourceName, newDataSourceName);  
newDatasource.ConnectionString = DatasourceCnxString.Text;  
if (impersonateServiceAccount.Checked)  
    newDatasource.ImpersonationInfo = new AMO.ImpersonationInfo(AMO.ImpersonationMode.ImpersonateServiceAccount);  
else  
{  
    if (String.IsNullOrEmpty(impersonateAccountUserName.Text))  
    {  
        MessageBox.Show(String.Format("Account User Name cannot be blank when using 'ImpersonateAccount' mode"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
        return;  
    }  
    newDatasource.ImpersonationInfo = new AMO.ImpersonationInfo(AMO.ImpersonationMode.ImpersonateAccount, impersonateAccountUserName.Text, impersonateAccountPassword.Text);  
}  
newDatasource.Update();  
  
```  
  
## <a name="tabular-amo-2012-sample"></a>Образец «Tabular AMO 2012»  
 Чтобы получить лучшее представление об использовании объектов AMO для создания и обработки представлений подключений, ознакомьтесь с образцом исходного кода Tabular AMO 2012. В частности, обратите внимание на следующий файл: Database.cs. Этот образец доступен на сайте Codeplex. Образец кода приведен только для иллюстрации описываемых здесь логических концепций и не должен использоваться в рабочей среде.  
  
  

