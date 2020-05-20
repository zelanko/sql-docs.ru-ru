---
title: Объект Command (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command
helpviewer_keywords:
- Command object [ADO]
ms.assetid: a02c22fb-542d-465e-a629-30fd59dcbebf
author: rothja
ms.author: jroth
ms.openlocfilehash: 6f6b2e68947959ecd497645d2290bb7acaa03f86
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760416"
---
# <a name="command-object-ado"></a>Объект Command (ADO)
Определяет конкретную команду, которую необходимо выполнить для источника данных.  
  
## <a name="remarks"></a>Примечания  
 Используйте объект **Command** , чтобы запрашивать базу данных и возвращать записи в объекте [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) , выполнять групповые операции или управлять структурой базы данных. В зависимости от функциональных возможностей поставщика некоторые коллекции **команд** , методы или свойства могут вызвать ошибку при ссылке.  
  
 С помощью коллекций, методов и свойств объекта **Command** можно выполнять следующие действия.  
  
-   Определите исполняемый текст команды (например, инструкцию SQL) со свойством [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) . Кроме того, для структур команд или запросов, отличных от простых строк (например, XML-запросов шаблонов), можно определить команду с помощью свойства [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) .  
  
-   При необходимости укажите диалект команды, используемый в **CommandText** или **CommandStream** со свойством [диалекта](../../../ado/reference/ado-api/dialect-property.md) .  
  
-   Определите параметризованные запросы или аргументы хранимой процедуры с объектами [параметров](../../../ado/reference/ado-api/parameter-object.md) и коллекцией [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) .  
  
-   Укажите, следует ли передавать имена параметров в поставщик с помощью свойства [NamedParameters](../../../ado/reference/ado-api/namedparameters-property-ado.md) .  
  
-   Выполните команду и верните объект **набора записей** , если он подходит для метода [EXECUTE](../../../ado/reference/ado-api/execute-method-ado-command.md) .  
  
-   Укажите тип команды со свойством [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) перед выполнением, чтобы оптимизировать производительность.  
  
-   Контролируйте, сохраняет ли поставщик подготовленную (или скомпилированную) версию команды перед выполнением с помощью [подготовленного](../../../ado/reference/ado-api/prepared-property-ado.md) свойства.  
  
-   Задайте количество секунд, в течение которых поставщик будет ожидать выполнения команды со свойством [CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md) .  
  
-   Свяжите открытое соединение с объектом **Command** , задав свойство [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) .  
  
-   Задайте свойство [Name](../../../ado/reference/ado-api/name-property-ado.md) , чтобы определить объект **команды** в качестве метода для связанного объекта [соединения](../../../ado/reference/ado-api/connection-object-ado.md) .  
  
-   Передайте объект **Command** свойству [Source](../../../ado/reference/ado-api/source-property-ado-recordset.md) **набора записей** для получения данных.  
  
-   Доступ к атрибутам, зависящим от поставщика, с коллекцией [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) .  
  
> [!NOTE]
>  Чтобы выполнить запрос без использования объекта **Command** , передайте строку запроса методу [EXECUTE](../../../ado/reference/ado-api/execute-method-ado-connection.md) объекта **Connection** или методу [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) объекта **Recordset** . Однако объект **команды** необходим, если нужно сохранить текст команды и повторно выполнить его, либо использовать параметры запроса.  
  
 Чтобы создать объект **команды** независимо от ранее определенного объекта **соединения** , задайте для его свойства **ActiveConnection** допустимую строку подключения. ADO по-прежнему создает объект **соединения** , но не присваивает его объектной переменной. Однако при связывании нескольких **командных** объектов с одним и тем же соединением следует явно создать и открыть объект **соединения** . При этом объект **соединения** назначается объектной переменной. Убедитесь, что объект **соединения** был успешно открыт, прежде чем присвоить его свойству **ActiveConnection** объекта **Command** , поскольку при назначении закрытого объекта **соединения** возникает ошибка. Если свойство **ActiveConnection** объекта **Command** не задано для этой объектной переменной, ADO создает новый объект **соединения** для каждого **командного** объекта, даже если используется та же строка подключения.  
  
 Чтобы выполнить **команду**, вызовите ее по свойству [Name](../../../ado/reference/ado-api/name-property-ado.md) для связанного объекта **соединения** . Для **команды** должно быть задано свойство **ActiveConnection** объекта **Connection** . Если **команда** имеет параметры, передайте их значения в качестве аргументов в метод.  
  
 Если в одном соединении выполняются два или более **командных** объектов, а любой из этих **команд** является хранимой процедурой с выходными параметрами, возникает ошибка. Для выполнения каждого объекта **команды** используйте отдельные соединения или отключите все остальные объекты **команд** из соединения.  
  
 Коллекция **Parameters** является элементом по умолчанию для объекта **Command** . В результате следующие два оператора кода эквивалентны.  
  
```  
objCmd.Parameters.Item(0)  
objCmd(0)  
```  
  
-   Объект **Command** не является надежным для сценариев.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Command](../../../ado/reference/ado-api/command-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Коллекция Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Приложение А. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md)
