---
title: Работа с типами данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: ff99a2d4d76067f7dfdc110ea8278fa8d1487799
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "84997177"
---
# <a name="working-with-data-types"></a>Работа с типами данных
  Данные поступают в виде различных типов и размеров, таких как строка определенной длины, число с конкретной точностью или определяемый пользователем тип, представляющий собой другой объект, со своим набором правил. <xref:Microsoft.SqlServer.Management.Smo.DataType>Объект классифицирует тип данных, чтобы их можно было правильно обработать с помощью [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Объект <xref:Microsoft.SqlServer.Management.Smo.DataType> связан с объектами, принимающими данные. Следующие управляющие объекты [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (SMO) принимают данные, которые должны быть определены свойством объекта <xref:Microsoft.SqlServer.Management.Smo.DataType>.  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Column>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedAggregateParameter>  
  
 Свойство `DataType` для объектов, принимающих данные, можно задать несколькими способами.  
  
-   Применение конструктора по умолчанию и явное определение свойств объекта <xref:Microsoft.SqlServer.Management.Smo.DataType>.  
  
-   Применение перегруженного конструктора и определение свойств объекта <xref:Microsoft.SqlServer.Management.Smo.DataType> как параметров.  
  
-   Определение встроенного параметра <xref:Microsoft.SqlServer.Management.Smo.DataType> в конструкторе объекта.  
  
-   Использование одного из статических членов класса <xref:Microsoft.SqlServer.Management.Smo.DataType>, например `Int`. В результате будет возвращен экземпляр объекта <xref:Microsoft.SqlServer.Management.Smo.DataType>.  
  
 Объект <xref:Microsoft.SqlServer.Management.Smo.DataType> имеет несколько свойств, описывающих тип данных. Например, свойство <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> задает тип данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Постоянные величины, представляющие типы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], приведены в перечислении <xref:Microsoft.SqlServer.Management.Smo.SqlDataType>. Это относится к таким типам данных, как `varchar`, `nchar`, `currency`, `integer`, `float` и `datetime`.  
  
 После установления типа данных необходимо задать для данных конкретные свойства. Например, если это тип `nchar`, необходимо задать в свойстве `Length` длину строковых данных. Тоже относится к числовым значениям, для которых необходимо задать точность и масштаб.  
  
 Типы данных <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> и <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> относятся к объектам, содержащим определение типа данных, созданного пользователем. Определяемый пользователем тип данных <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> основан на типах данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из перечисления <xref:Microsoft.SqlServer.Management.Smo.SqlDataType>. Объект <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> основан на [!INCLUDE[msCoName](../../../includes/msconame-md.md)] типах данных .NET. Обычно эти данные представляют собой данные конкретного типа, часто используемые повторно в базе данных, поскольку этого требуют бизнес-правила, определяемые организацией. Например, компания, которая проводит сделки с использованием нескольких валют, может использовать тип данных, предусматривающий хранение денежной суммы и кода валюты.  
  
 Перечисление <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> содержит список всех типов данных, поддерживаемых в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="examples"></a>Примеры  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-basic"></a>Создание объекта DataType со спецификацией в конструкторе объекта на языке Visual Basic  
 Этот пример кода показывает использование конструктора для создания экземпляров типов данных на основе различных типов данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Типы <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> и типы XML требуют использования имени для идентификации объекта.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDataTypes1](SMO How to#SMO_VBDataTypes1)]  -->  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-c"></a>Создание объекта DataType со спецификацией в конструкторе объекта на языке Visual C#  
 Этот пример кода показывает использование конструктора для создания экземпляров типов данных на основе различных типов данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Типы <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> и типы XML требуют использования имени для идентификации объекта.  
  
```  
{   
//Declare a DataType object variable and define the data type in the constructor.   
DataType dt;   
//For the decimal data type the following two arguments specify precision, and scale.   
dt = new DataType(SqlDataType.Decimal, 10, 2);   
}  
```  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-basic"></a>Создание объекта DataType с применением конструктора по умолчанию на языке Visual Basic  
 Этот пример кода показывает использование конструктора для создания экземпляров типов данных на основе различных типов данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . После этого с помощью свойств задается тип данных.  
  
 **Примечание** . <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> Для всех типов XML, и требуется значение имени для указания объекта.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDataTypes2](SMO How to#SMO_VBDataTypes2)]  -->  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-c"></a>Создание объекта DataType с применением конструктора по умолчанию на языке Visual C#  
 Этот пример кода показывает использование конструктора для создания экземпляров типов данных на основе различных типов данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . После этого с помощью свойств задается тип данных.  
  
 **Примечание** . <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> Для всех типов XML, и требуется значение имени для указания объекта.  
  
```  
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
  
  
