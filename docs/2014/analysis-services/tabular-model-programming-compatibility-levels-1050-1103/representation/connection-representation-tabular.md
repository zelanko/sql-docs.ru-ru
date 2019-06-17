---
title: Представление соединения (табличное) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 4b410b16-d36e-4185-bb20-922e66e5e2b7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ffd99068db329ea8e9066c6bd9508dc13f239690
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62757762"
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
 Чтобы получить представление о том, как использовать объекты AMO для создания и обработки представлений подключений, см. в статье исходный код в образце Tabular AMO 2012; в частности, проверьте в следующий файл: Database.cs. Этот образец доступен на сайте Codeplex. Образец кода приведен только для иллюстрации описываемых здесь логических концепций и не должен использоваться в рабочей среде.  
  
  
