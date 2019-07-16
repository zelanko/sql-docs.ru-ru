---
title: Работа с типами данных | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- DataType object
- SQL Server Management Objects, data types
- data types [SMO]
- SMO [SQL Server], data types
ms.assetid: 1e0e736a-c709-4d89-aeb2-b32dcfd641fa
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f55cb64c052978bd6ef36edecd7354f4d012e5b7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68098182"
---
# <a name="working-with-data-types"></a>Работа с типами данных
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Данные поступают в виде различных типов и размеров, таких как строка определенной длины, число с конкретной точностью или определяемый пользователем тип, представляющий собой другой объект, со своим набором правил. <xref:Microsoft.SqlServer.Management.Smo.DataType> Классифицирует типы данных, чтобы оно могло быть обработано правильно по [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Объект <xref:Microsoft.SqlServer.Management.Smo.DataType> связан с объектами, принимающими данные. Следующие управляющие объекты [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (SMO) принимают данные, которые должны быть определены свойством объекта <xref:Microsoft.SqlServer.Management.Smo.DataType>.  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Column>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedAggregateParameter>  
  
 Свойство **DataType** для объектов, принимающих данные, можно задать несколькими способами.  
  
-   Применение конструктора по умолчанию и явное определение свойств объекта <xref:Microsoft.SqlServer.Management.Smo.DataType>.  
  
-   Применение перегруженного конструктора и определение свойств объекта <xref:Microsoft.SqlServer.Management.Smo.DataType> как параметров.  
  
-   Определение встроенного параметра <xref:Microsoft.SqlServer.Management.Smo.DataType> в конструкторе объекта.  
  
-   Используйте один из статических членов <xref:Microsoft.SqlServer.Management.Smo.DataType> классов, например **Int**. В результате будет возвращен экземпляр объекта <xref:Microsoft.SqlServer.Management.Smo.DataType>.  
  
 Объект <xref:Microsoft.SqlServer.Management.Smo.DataType> имеет несколько свойств, описывающих тип данных. Например, свойство <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> задает тип данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Постоянные величины, представляющие типы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], приведены в перечислении <xref:Microsoft.SqlServer.Management.Smo.SqlDataType>. Это относится к таким типам данных, как **varchar**, **nchar**, **currency**, **integer**, **float**и **datetime**.  
  
 После установления типа данных необходимо задать для данных конкретные свойства. Например, если это тип **nchar** , необходимо задать в свойстве **Length** длину строковых данных. Тоже относится к числовым значениям, для которых необходимо задать точность и масштаб.  
  
 Типы данных <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> и <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> относятся к объектам, содержащим определение типа данных, созданного пользователем. Определяемый пользователем тип данных <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> основан на типах данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из перечисления <xref:Microsoft.SqlServer.Management.Smo.SqlDataType>. <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> Основан на [!INCLUDE[msCoName](../../../includes/msconame-md.md)] типы данных .NET. Обычно эти данные представляют собой данные конкретного типа, часто используемые повторно в базе данных, поскольку этого требуют бизнес-правила, определяемые организацией. Например, компания, которая проводит сделки с использованием нескольких валют, может использовать тип данных, предусматривающий хранение денежной суммы и кода валюты.  
  
 Перечисление <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> содержит список всех типов данных, поддерживаемых в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="examples"></a>Примеры  
Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в разделе [Visual C создайте&#35; проекта SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-basic"></a>Создание объекта DataType со спецификацией в конструкторе объекта на языке Visual Basic  
 Этот пример кода показывает использование конструктора для создания экземпляров типов данных на основе различных типов данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Типы <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> и типы XML требуют использования имени для идентификации объекта.  
  
```VBNET
'Declare a DataType object variable and define the data type in the constructor.
Dim dt As DataType
'For the decimal data type the following two arguments specify precision, and scale.
dt = New DataType(SqlDataType.Decimal, 10, 2)
``` 
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-c"></a>Создание объекта DataType со спецификацией в конструкторе объекта на языке Visual C#  
 Этот пример кода показывает использование конструктора для создания экземпляров типов данных на основе различных типов данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Типы <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> и типы XML требуют использования имени для идентификации объекта.  
  
```csharp  
{   
//Declare a DataType object variable and define the data type in the constructor.   
DataType dt;   
//For the decimal data type the following two arguments specify precision, and scale.   
dt = new DataType(SqlDataType.Decimal, 10, 2);   
}  
```  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-basic"></a>Создание объекта DataType с применением конструктора по умолчанию на языке Visual Basic  
 Этот пример кода показывает использование конструктора для создания экземпляров типов данных на основе различных типов данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . После этого с помощью свойств задается тип данных.  
  
 **Примечание** <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, и типы XML требуют использования имени для идентификации объекта.  
  
```VBNET
'Declare and create a DataType object variable.
Dim dt As DataType
dt = New DataType
'Define the data type by setting the SqlDataType property.
dt.SqlDataType = SqlDataType.VarChar
'The VarChar data type requires a value for the MaximumLength property.
dt.MaximumLength = 100
```
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-c"></a>Создание объекта DataType с применением конструктора по умолчанию на языке Visual C#  
 Этот пример кода показывает использование конструктора для создания экземпляров типов данных на основе различных типов данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . После этого с помощью свойств задается тип данных.  
  
 **Примечание** <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, и типы XML требуют использования имени для идентификации объекта.  
  
```csharp  
{   
//Declare and create a DataType object variable.   
DataType dt;   
dt = new DataType();   
//Define the data type by setting the SqlDataType property.   
dt.SqlDataType = SqlDataType.VarChar;   
//The VarChar data type requires a value for the MaximumLength property.   
dt.MaximumLength = 100;   
}  
```  
  
  
