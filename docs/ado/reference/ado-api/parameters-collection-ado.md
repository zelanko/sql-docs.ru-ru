---
title: Коллекция Parameters (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::get_Parameters
- Command15::Parameters
- Command15::GetParameters
helpviewer_keywords:
- Parameters collection [ADO]
ms.assetid: 497cae10-3913-422a-9753-dcbb0a639b1b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a23b67141c7c07845438ed43f00d3124043a53c4
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66704112"
---
# <a name="parameters-collection-ado"></a>Коллекция Parameters (ADO)
Содержит все [параметр](../../../ado/reference/ado-api/parameter-object.md) объектов [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта.  
  
## <a name="remarks"></a>Примечания  
 Объект **команда** объект имеет **параметры** состоит из коллекции **параметр** объектов.  
  
 С помощью [обновить](../../../ado/reference/ado-api/refresh-method-ado.md) метод **команда** объекта **параметры** коллекции извлекает сведения о параметрах поставщика для хранимой процедуры или параметризованного запроса указанный в **команда** объекта. Некоторые поставщики не поддерживают вызовы хранимой процедуры или параметризованные запросы; вызов **обновить** метод **параметры** коллекции при использовании такой поставщик возвратит ошибку.  
  
 Если вы не определили собственный **параметр** объектов, а доступ к **параметры** коллекции перед вызовом **обновить** метод, автоматически вызывает ADO метод и заполнения коллекции для вас.  
  
 Можно свести к минимуму вызовы поставщика для повышения производительности, если вы знаете, свойства параметров, связанный с хранимой процедуры или параметризированного запроса, которые должны вызываться. Используйте [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) метод для создания **параметр** объектов с соответствующими параметрами свойств и используйте [Append](../../../ado/reference/ado-api/append-method-ado.md) метод, чтобы добавить их в  **Параметры** коллекции. Это позволяет задать и получить значения параметров не нужно звонить поставщика сведения о параметре. При написании поставщику, который не предоставляет сведения о параметрах, необходимо вручную заполнить **параметры** коллекции, с помощью этого метода, чтобы иметь возможность использовать параметры вообще. Используйте [удалить](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md) способ удаления **параметр** объектов из **параметры** коллекции, при необходимости.  
  
 Объекты в **параметры** коллекцию **записей** перейдите за пределы области действия (таким образом становится недоступной) при **записей** закрыт.  
  
 При вызове хранимой процедуры с **команда**, возвращаемое значение или выходной параметр хранимой процедуры, извлекается следующим образом:  
  
1.  При вызове хранимой процедуры, которая не имеет параметров, **обновить** метод **параметры** коллекции должен вызываться перед вызовом **Execute** метод **Команда** объекта.  
  
2.  При вызове хранимой процедуры с параметрами и явным образом добавления параметра **параметры** коллекции с **Append**, возвращаемое значение или выходной параметр следует добавлять к **Параметры** коллекции. Возвращаемое значение сначала должен быть добавлен к **параметры** коллекции. Используйте **Append** можно добавить другие параметры в **параметры** коллекции в порядке определения. Например хранимая процедура SPWithParam имеет два параметра. Первый параметр, *InParam*, определяется как adVarChar (20) входного параметра, а второй параметр, *OutParam*, выходной параметр определен как adVarChar (20). Можно получить возвращаемое значение/выходной параметр следующим кодом.  
  
    ```vb
    ' Open Connection Conn  
    set ccmd = CreateObject("ADODB.Command")  
    ccmd.Activeconnection= Conn  
  
    ccmd.CommandText="SPWithParam"  
    ccmd.commandType = 4 'adCmdStoredProc  
  
    ccmd.parameters.Append ccmd.CreateParameter(, adInteger, adParamReturnValue, , NULL)   ' return value  
    ccmd.parameters.Append ccmd.CreateParameter("InParam", adVarChar, adParamInput, 20, "hello world")   ' input parameter  
    ccmd.parameters.Append ccmd.CreateParameter("OutParam", adVarChar, adParamOutput, 20, NULL)   ' output parameter  
  
    ccmd.execute()  
  
    ' Access ccmd.parameters(0) as return value of this stored procedure  
    ' Access ccmd.parameters("OutParam") as the output parameter of this stored procedure.  
  
    ```  
  
3.  При вызове хранимой процедуры с параметрами и настройка параметров путем вызова **элемента** метод **параметры** можно коллекции, возвращаемое значение или выходной параметр хранимой процедуры получить из **параметры** коллекции. Например хранимая процедура SPWithParam имеет два параметра. Первый параметр, *InParam*, определяется как adVarChar (20) входного параметра, а второй параметр, *OutParam*, выходной параметр определен как adVarChar (20). Можно получить возвращаемое значение/выходной параметр следующим кодом.  
  
    ```vb
    ' Open Connection Conn  
    set ccmd = CreateObject("ADODB.Command")  
    ccmd.Activeconnection= Conn  
  
    ccmd.CommandText="SPWithParam"  
    ccmd.commandType = 4 'adCmdStoredProc  
  
    ccmd.parameters.Item("InParam").value = "hello world" ' input parameter  
    ccmd.execute()  
  
    ' Access ccmd.parameters(0) as return value of stored procedure  
    ' Access ccmd.parameters(2) or ccmd.parameters("OutParam") as the output parameter.  
    ```  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Параметры коллекции свойства, методы и события](../../../ado/reference/ado-api/parameters-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Метод append (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [Метод CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)
