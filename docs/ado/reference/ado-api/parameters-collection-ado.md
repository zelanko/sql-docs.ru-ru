---
description: Коллекция Parameters (ADO)
title: Коллекция Parameters (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: bad2570c368e469afeb7c69e4f283bdbdfe04674
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990125"
---
# <a name="parameters-collection-ado"></a>Коллекция Parameters (ADO)
Содержит все объекты [параметров](./parameter-object.md) объекта [Command](./command-object-ado.md) .  
  
## <a name="remarks"></a>Remarks  
 Объект **Command** содержит коллекцию **Parameters** , состоящие из объектов **параметров** .  
  
 При использовании метода [Refresh](./refresh-method-ado.md) в коллекции **Parameters** объекта **Command** извлекаются сведения о параметрах поставщика для хранимой процедуры или параметризованного запроса, указанного в объекте **Command** . Некоторые поставщики не поддерживают вызовы хранимых процедур или параметризованные запросы; вызов метода **Refresh** для коллекции **Parameters** при использовании такого поставщика возвратит ошибку.  
  
 Если вы не определили собственные объекты **параметров** и хотите получить доступ к коллекции **Parameters** перед вызовом метода **Refresh** , ADO автоматически вызовет метод и заполнит коллекцию.  
  
 Можно уменьшить число вызовов поставщика, чтобы повысить производительность, если известно, какие свойства параметров связаны с хранимой процедурой или параметризованным запросом, который необходимо вызвать. Используйте метод [CreateParameter](./createparameter-method-ado.md) для создания объектов **параметров** с соответствующими параметрами свойств и используйте метод [append](./append-method-ado.md) , чтобы добавить их в коллекцию **Parameters** . Это позволяет задавать и возвращать значения параметров без вызова поставщика для сведений о параметрах. При записи в поставщик, который не предоставляет сведения о параметрах, необходимо вручную заполнить коллекцию **Parameters** с помощью этого метода, чтобы иметь возможность использовать параметры вообще. При необходимости удалите объекты **параметров** из коллекции **Parameters** с помощью метода [Delete](./delete-method-ado-parameters-collection.md) .  
  
 Объекты в коллекции **Parameters** **набора записей** выходят за пределы области действия (поэтому становятся недоступными) при закрытии **набора записей** .  
  
 При вызове хранимой процедуры с **командой**возвращаемое значение или выходной параметр хранимой процедуры извлекается следующим образом:  
  
1.  При вызове хранимой процедуры, не имеющей параметров, метод **Refresh** коллекции **Parameters** должен вызываться перед вызовом метода **EXECUTE** для объекта **Command** .  
  
2.  При вызове хранимой процедуры с параметрами и явном добавлении параметра в коллекцию **Parameters** с **добавлением**возвращаемого значения или выходного параметра в коллекцию **Parameters** следует добавить. Возвращаемое значение должно сначала быть добавлено в коллекцию **Parameters** . Используйте **append** , чтобы добавить другие параметры в коллекцию **Parameters** в порядке определения. Например, хранимая процедура Спвиспарам имеет два параметра. Первый параметр, *param*, — это входной параметр, определенный как адварчар (20), а второй параметр, *param*, — это выходной параметр, определенный как адварчар (20). Возвращаемое значение и выходной параметр можно получить с помощью следующего кода.  
  
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
  
3.  При вызове хранимой процедуры с параметрами и настройке параметров путем вызова метода **Item** для коллекции **Parameters** возвращаемое значение или выходной параметр хранимой процедуры можно получить из коллекции **Parameters** . Например, хранимая процедура Спвиспарам имеет два параметра. Первый параметр, *param*, — это входной параметр, определенный как адварчар (20), а второй параметр, *param*, — это выходной параметр, определенный как адварчар (20). Возвращаемое значение и выходной параметр можно получить с помощью следующего кода.  
  
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
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события коллекции Parameters](./parameters-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Append (ADO)](./append-method-ado.md)   
 [Метод CreateParameter (ADO)](./createparameter-method-ado.md)   
 [Объект Parameter](./parameter-object.md)