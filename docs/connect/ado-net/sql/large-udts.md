---
title: Большие UDT
description: Здесь демонстрируется получение данных из UDT с большими значениями, представленных в SQL Server 2008.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: e572b8fcf1550562c7a9f1841eec1c311f18c3f8
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896708"
---
# <a name="large-udts"></a>Большие UDT

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Определяемые пользователем типы призваны дать разработчику возможность расширить серверную систему скалярных типов путем хранения объектов среды CLR в базе данных SQL Server. Определяемые пользователем типы могут содержать несколько элементов, и их поведение может отличаться от традиционных псевдонимов типов данных, которые состоят из одного системного типа данных SQL Server.  
  
Ранее размер определяемых пользователем типов был ограничен 8 килобайтами. Это ограничение было снято в SQL Server 2008 для определяемых пользователем типов, имеющих формат <xref:Microsoft.Data.SqlClient.Server.Format.UserDefined>.  
  
Полную документацию по пользовательским типам см. в разделе [Определяемые пользователем типы данных CLR](https://go.microsoft.com/fwlink/?LinkId=98366) в электронной документации по SQL Server.
  
## <a name="retrieving-udt-schemas-using-getschema"></a>Получение схем пользовательского типа с помощью GetSchema  
Метод <xref:Microsoft.Data.SqlClient.SqlConnection.GetSchema%2A> <xref:Microsoft.Data.SqlClient.SqlConnection> возвращает сведения о схеме базы данных в <xref:System.Data.DataTable>.
  
### <a name="getschematable-column-values-for-udts"></a>Значения столбцов GetSchemaTable для UDT  
Метод <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> <xref:Microsoft.Data.SqlClient.SqlDataReader> возвращает <xref:System.Data.DataTable>, описывающее метаданные столбца. В следующей таблице описаны различия в метаданных столбцов для больших пользовательских типов данных между SQL Server 2005 и SQL Server 2008.  
  
|Столбец SqlDataReader|SQL Server 2005|SQL Server 2008 и более поздние версии|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|Различается|Различается|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|Экземпляр UDT|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|Экземпляр UDT|  
|`ProviderType`|21 (`SqlDbType.VarBinary`)|29 (`SqlDbType.Udt`)|  
|`NonVersionedProviderType`|29 (`SqlDbType.Udt`)|29 (`SqlDbType.Udt`)|  
|`DataTypeName`|`SqlDbType.VarBinary`|Имя из трех частей, указанное как *Database.SchemaName.TypeName*.|  
|`IsLong`|Различается|Различается|  
  
## <a name="sqldatareader-considerations"></a>Рекомендации по SqlDataReader  
Объект <xref:Microsoft.Data.SqlClient.SqlDataReader> в SQL Server 2008 был расширен для поддержки загрузки значений определяемых пользователем типов данных большого размера. Как большие значения пользовательского типа обрабатываются <xref:Microsoft.Data.SqlClient.SqlDataReader>, зависит от используемой версии SQL Server, а также от `Type System Version`, указанного в строке подключения. Дополнительные сведения см. в разделе <xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
Следующие методы <xref:Microsoft.Data.SqlClient.SqlDataReader> будут возвращать <xref:System.Data.SqlTypes.SqlBinary> вместо пользовательского типа, если для `Type System Version` установлено значение SQL Server 2005:  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
Следующие методы будут возвращать массив `Byte[]` вместо пользовательского типа, если для `Type System Version` установлено значение SQL Server 2005:  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
Обратите внимание, что для текущей версии ADO.NET никакие преобразования не выполняются.  
  
## <a name="specifying-sqlparameters"></a>Указание SqlParameters  
Следующие свойства <xref:Microsoft.Data.SqlClient.SqlParameter> были расширены для работы с большими пользовательскими типами.  
  
|Свойство SqlParameter|Description|  
|---------------------------|-----------------|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Value%2A>|Возвращает или задает объект, представляющий значение параметра. Значение по умолчанию — NULL. Свойством может быть `SqlBinary`, `Byte[]` или управляемый объект.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.SqlValue%2A>|Возвращает или задает объект, представляющий значение параметра. Значение по умолчанию — NULL. Свойством может быть `SqlBinary`, `Byte[]` или управляемый объект.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Size%2A>|Возвращает или задает размер значения параметра для разрешения. Значение по умолчанию — 0. Свойство может быть целым числом, представляющим размер значения параметра. Для больших определяемых пользователем типов оно может равняться действительному размеру определяемого пользователем типа или иметь значение –1 — для неизвестных.|  
  
## <a name="retrieving-data-example"></a>Пример извлечения данных  
В следующем фрагменте кода показано, как получить большие данные пользовательского типа. Переменная `connectionString` предполагает допустимое соединение с базой данных SQL Server, а переменная `commandString` предполагает, что допустимая инструкция SELECT со столбцом первичного ключа указана первой.  
  
```csharp  
using (SqlConnection connection = new SqlConnection(   
    connectionString, commandString))  
{  
  connection.Open();  
  SqlCommand command = new SqlCommand(commandString);  
  SqlDataReader reader = command.ExecuteReader();  
  while (reader.Read())  
  {  
    // Retrieve the value of the Primary Key column.  
    int id = reader.GetInt32(0);  
  
    // Retrieve the value of the UDT.  
    LargeUDT udt = (LargeUDT)reader[1];  
  
    // You can also use GetSqlValue and GetValue.  
    // LargeUDT udt = (LargeUDT)reader.GetSqlValue(1);  
    // LargeUDT udt = (LargeUDT)reader.GetValue(1);  
  
    Console.WriteLine(  
     "ID={0} LargeUDT={1}", id, udt);  
  }  
reader.close  
}  
```  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Двоичные данные и данные больших значений SQL Server](sql-server-binary-large-value-data.md)
 