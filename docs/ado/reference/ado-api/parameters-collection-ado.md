---
title: Коллекция параметров (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::get_Parameters
- Command15::Parameters
- Command15::GetParameters
helpviewer_keywords:
- Parameters collection [ADO]
ms.assetid: 497cae10-3913-422a-9753-dcbb0a639b1b
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7c59411e1aeeaa32e2b1904e2503b26a92c829b
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280672"
---
# <a name="parameters-collection-ado"></a>Коллекция параметров (ADO)
Содержит все [параметр](../../../ado/reference/ado-api/parameter-object.md) объектов [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта.  
  
## <a name="remarks"></a>Примечания  
 Объект **команда** объект имеет **параметры** коллекцию, состоящую из **параметр** объектов.  
  
 С помощью [обновление](../../../ado/reference/ado-api/refresh-method-ado.md) метод **команда** объекта **параметры** коллекции получает сведения о параметрах поставщика для хранимой процедуры или параметризованного запроса указанный в **команда** объекта. Некоторые поставщики не поддерживают вызовы хранимой процедуры или параметризованные запросы; вызов **обновление** метод **параметры** коллекции при использовании такой поставщик возвратит ошибку.  
  
 Если вы не определили собственную **параметр** объектов, а доступ к **параметры** коллекции перед вызовом **обновление** метод, автоматически вызывает ADO метод и заполнения в коллекции.  
  
 Можно свести к минимуму вызовы поставщика для повышения производительности, если вы знаете, свойства параметров, связанных с помощью хранимой процедуры или параметризированного запроса, которые требуется вызвать. Используйте [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) метод для создания **параметр** объектов с соответствующими параметрами свойств, а также с помощью [Append](../../../ado/reference/ado-api/append-method-ado.md) метод, чтобы добавить их в  **Параметры** коллекции. Это позволяет задать и возвращать значения параметров без вызова метода поставщика для получения параметров. При создании поставщика, который не предоставляет сведения о параметрах вручную заполнять **параметры** коллекции с помощью этого метода, чтобы иметь возможность использовать параметры вообще. Используйте [удаление](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md) метод для удаления **параметр** объектов из **параметры** коллекцию при необходимости.  
  
 Объекты в **параметры** коллекцию **записей** перейдите за пределы области (поэтому недоступности) при **записей** закрыт.  
  
 При вызове хранимой процедуры с **команда**, возвращаемое значение или выходной параметр хранимой процедуры, извлекается следующим образом:  
  
1.  При вызове хранимой процедуры, которая не имеет параметров, **обновления** метод **параметры** коллекции следует вызывать до вызова метода **Execute** метод **Команда** объекта.  
  
2.  При вызове хранимой процедуры с параметрами и явным образом при добавлении параметра **параметры** коллекции с **Append**, возвращаемое значение или выходной параметр должен быть дополнен **Параметры** коллекции. Возвращаемое значение сначала должен быть добавлен к **параметры** коллекции. Используйте **Append** можно добавить другие параметры в **параметры** коллекции в порядке определения. Например хранимая процедура SPWithParam имеет два параметра. Первый параметр *InParam*, определяется как adVarChar (20) входного параметра, а второй параметр *OutParam*, выходной параметр определен как adVarChar (20). Можно получить возвращаемое значение или выходной параметр следующим кодом.  
  
    ```  
    ' Open Connection Conn  
    set ccmd = CreateObject("ADODB.Command")  
    ccmd.Activeconnection= Conn  
  
    ccmd.CommandText="SPWithParam"  
    ccmd.commandType = 4 'adCmdStoredProc  
  
    ccmd.parameters.Append ccmd.CreateParameter(, adInteger, adParamReturnValue, , NULL)   ' return value  
    ccmd.parameters.Append ccmd.CreateParameter("InParam", adVarChar, adParamInput, 20, "hello world")   ' input parameter  
    ccmd.parameters.Append ccmd.CreateParameter("OutParam", adVarChar, adParamOuput, 20, NULL)   ' output parameter  
  
    ccmd.execute()  
  
    ' Access ccmd.parameters(0) as return value of this stored procedure  
    ' Access ccmd.parameters("OutParam") as the output parameter of this stored procedure.  
  
    ```  
  
3.  При вызове хранимой процедуры с параметрами и настройка параметров путем вызова **элемент** метод **параметры** коллекции, возвращаемое значение или выходной параметр хранимой процедуры можно получить из **параметры** коллекции. Например хранимая процедура SPWithParam имеет два параметра. Первый параметр *InParam*, определяется как adVarChar (20) входного параметра, а второй параметр *OutParam*, выходной параметр определен как adVarChar (20). Можно получить возвращаемое значение или выходной параметр следующим кодом.  
  
    ```  
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
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства коллекции параметров, методы и события](../../../ado/reference/ado-api/parameters-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Append-метод (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [Метод CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)
