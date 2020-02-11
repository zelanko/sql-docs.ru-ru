---
title: Общие сведения о настраиваемых атрибутах интеграции со средой CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- custom attributes [CLR integration]
- attributes [CLR integration]
- common language runtime [SQL Server], attributes
- database objects [CLR integration], custom attributes
- building database objects [CLR integration], custom attributes
ms.assetid: ecf5c097-0972-48e2-a9c0-b695b7dd2820
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8df7881dd5f38935628cb6653d57763a8846e60f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62781109"
---
# <a name="overview-of-clr-integration-custom-attributes"></a>Общие сведения о пользовательских атрибутах интеграции со средой CLR
  В среде CLR [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] допускается использование описательных ключевых слов, именуемых атрибутами. Эти атрибуты содержат дополнительную информацию по многим элементам, таким как методы и классы. Эти атрибуты сохраняются в сборке с метаданными объекта и могут быть использованы для описания кода другим инструментальным средствам разработки или для изменения поведения на этапе выполнения внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 При регистрации подпрограммы среды CLR в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] получает набор свойств этой подпрограммы. Эти свойства подпрограммы определяют возможности подпрограммы и в частности указывают на то, может ли она быть индексирована. Так, если свойству `DataAccess` задается значение `DataAccessKind.Read`, тем самым открывается возможность обращения к данным из пользовательских таблиц [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] внутри функции CLR. В следующем примере показан простой случай, в котором `DataAccess` свойство задано для упрощения доступа к данным из пользовательской таблицы **Table1**.  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
  
public partial class UserDefinedFunctions  
{  
    [SqlFunction(DataAccess = DataAccessKind.Read)]  
    public static string func1()  
    {  
        // Open a connection and create a command  
        SqlConnection conn = new SqlConnection("context connection = true");  
        conn.Open();  
        SqlCommand cmd = conn.CreateCommand();  
        cmd.CommandText = "SELECT str_val FROM table1 WHERE int_val = 10";  
        // where table1 is a user table  
        // Execute this command   
        SqlDataReader rd = cmd.ExecuteReader();  
        // Set string ret_val to str_val returned from the query  
        string ret_val = rd.GetValue(0).ToString();  
        rd.Close();  
        return ret_val;  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Public partial Class UserDefinedFunctions  
    <SqlFunction(DataAccess = DataAccessKind.Read)> _   
    Public Shared Function func1() As String  
        ' Open a connection and create a command  
        Dim conn As SqlConnection = New SqlConnection("context connection = true")   
        conn.Open()  
        Dim cmd As SqlCommand =  conn.CreateCommand()   
        cmd.CommandText = "SELECT str_val FROM table1 WHERE int_val = 10"  
        ' where table1 is a user table  
        ' Execute this command   
        Dim rd As SqlDataReader =  cmd.ExecuteReader()   
        ' Set string ret_val to str_val returned from the query  
        Dim ret_val As String =  rd.GetValue(0).ToString()   
        rd.Close()  
        Return ret_val  
    End Function  
End Class  
```  
  
 Что же касается подпрограмм [!INCLUDE[tsql](../../includes/tsql-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] получает свойства подпрограмм непосредственно из их определений. Сервер не анализирует тексты подпрограмм CLR для получения этих свойств. Вместо этого можно использовать пользовательские атрибуты для классов и членов классов, реализованных в языке [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
 Пользовательские атрибуты, необходимые для подпрограмм CLR, пользовательских типов и агрегатов, определяются в пространстве имен `Microsoft.SqlServer.Server`.  
  
## <a name="see-also"></a>См. также:  
 [Пользовательские атрибуты для подпрограмм среды CLR](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md)  
  
  
