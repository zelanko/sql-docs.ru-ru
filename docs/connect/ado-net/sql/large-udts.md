---
title: Большие UDT
description: Демонстрирует получение данных из определяемых пользователем типов больших значений, представленных в SQL Server 2008.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 4ea2c0002ceb01606cdf51f04246abcdc74429e0
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452153"
---
# <a name="large-udts"></a>Большие UDT

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Определяемые пользователем типы призваны дать разработчику возможность расширить серверную систему скалярных типов путем хранения объектов среды CLR в базе данных SQL Server. Определяемые пользователем типы могут содержать несколько элементов, и их поведение может отличаться от традиционных псевдонимов типов данных, которые состоят из одного системного типа данных SQL Server.  
  
Ранее размер определяемых пользователем типов был ограничен 8 килобайтами. Это ограничение было снято в SQL Server 2008 для определяемых пользователем типов, имеющих формат <xref:Microsoft.Data.SqlClient.Server.Format.UserDefined>.  
  
Полную документацию по определяемым пользователем типам см. в разделе [определяемые пользователем типы данных CLR](https://go.microsoft.com/fwlink/?LinkId=98366) из электронная документация на SQL Server.
  
## <a name="retrieving-udt-schemas-using-getschema"></a>Получение схем определяемого пользователем типа с помощью GetSchema  
Метод <xref:Microsoft.Data.SqlClient.SqlConnection.GetSchema%2A> <xref:Microsoft.Data.SqlClient.SqlConnection> возвращает сведения о схеме базы данных в <xref:System.Data.DataTable>.
  
### <a name="getschematable-column-values-for-udts"></a>GetSchemaTable значений столбцов для определяемых пользователем типов  
Метод <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> <xref:Microsoft.Data.SqlClient.SqlDataReader> возвращает <xref:System.Data.DataTable>, описывающее метаданные столбца. В следующей таблице описаны различия в метаданных столбцов для больших определяемых пользователем типов данных в диапазоне от SQL Server 2005 до SQL Server 2008.  
  
|Столбец SqlDataReader|SQL Server 2005|SQL Server 2008 и более поздние версии|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|Различается|Различается|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|Экземпляр определяемого пользователем типа|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|Экземпляр определяемого пользователем типа|  
|`ProviderType`|21 (`SqlDbType.VarBinary`)|29 (`SqlDbType.Udt`)|  
|`NonVersionedProviderType`|29 (`SqlDbType.Udt`)|29 (`SqlDbType.Udt`)|  
|`DataTypeName`|`SqlDbType.VarBinary`|Имя из трех частей, указанное как *Database.SchemaName.TypeName*.|  
|`IsLong`|Различается|Различается|  
  
## <a name="sqldatareader-considerations"></a>Рекомендации по SqlDataReader  
Объект <xref:Microsoft.Data.SqlClient.SqlDataReader> в SQL Server 2008 был расширен для поддержки загрузки значений определяемых пользователем типов данных большого размера. Как большие значения определяемого пользователем типа обрабатываются <xref:Microsoft.Data.SqlClient.SqlDataReader> зависит от используемой версии SQL Server, а также от `Type System Version`, указанных в строке подключения. Дополнительные сведения см. в разделе <xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
Следующие методы <xref:Microsoft.Data.SqlClient.SqlDataReader> будут возвращать <xref:System.Data.SqlTypes.SqlBinary> вместо определяемого пользователем типа, если для `Type System Version` установлено значение SQL Server 2005:  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
Следующие методы возвращают массив `Byte[]` вместо определяемого пользователем типа, если `Type System Version` имеет значение SQL Server 2005:  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
Обратите внимание, что для текущей версии ADO.NET никакие преобразования не выполняются.  
  
## <a name="specifying-sqlparameters"></a>Указание Склпараметерс  
Следующие свойства <xref:Microsoft.Data.SqlClient.SqlParameter> были расширены для работы с большими определяемыми пользователем типами.  
  
|Свойство SqlParameter|Описание|  
|---------------------------|-----------------|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Value%2A>|Возвращает или задает объект, представляющий значение параметра. Значение по умолчанию — NULL. Свойством может быть `SqlBinary`, `Byte[]` или управляемый объект.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.SqlValue%2A>|Возвращает или задает объект, представляющий значение параметра. Значение по умолчанию — NULL. Свойством может быть `SqlBinary`, `Byte[]` или управляемый объект.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Size%2A>|Возвращает или задает размер значения параметра для разрешения. Значение по умолчанию — 0. Свойство может быть целым числом, представляющим размер значения параметра. Для больших определяемых пользователем типов оно может равняться действительному размеру определяемого пользователем типа или иметь значение –1 — для неизвестных.|  
  
## <a name="retrieving-data-example"></a>Пример получения данных  
В следующем фрагменте кода показано, как получить большие данные определяемого пользователем типа. `connectionString` ая переменная предполагает допустимое соединение с SQL Serverной базой данных, а переменная `commandString` предполагает, что правильно указана допустимая инструкция SELECT со столбцом первичного ключа.  
  
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
