---
title: Объект Connection (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection
helpviewer_keywords:
- Connection object [ADO]
ms.assetid: ef6b1824-5b12-43db-89d7-8f3d13896d4d
author: rothja
ms.author: jroth
ms.openlocfilehash: 49a270f143e57c1e093ac94732b67b6424c88607
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760300"
---
# <a name="connection-object-ado"></a>Объект Connection (ADO)
Представляет открытое подключение к источнику данных.  
  
## <a name="remarks"></a>Remarks  
 Объект **Connection** представляет уникальный сеанс с источником данных. В системе базы данных клиента или сервера она может быть эквивалентна фактическому сетевому подключению к серверу. В зависимости от функциональности, поддерживаемой поставщиком, некоторые коллекции, методы или свойства объекта **соединения** могут быть недоступны.  
  
 С помощью коллекций, методов и свойств объекта **Connection** можно выполнять следующие действия.  
  
-   Настройте подключение перед его открытием с помощью свойств [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md), [ConnectionTimeout](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)и [mode](../../../ado/reference/ado-api/mode-property-ado.md) . **ConnectionString** — это свойство объекта **Connection** по умолчанию.  
  
-   Задайте для свойства [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) значение Client, чтобы вызвать [службу Microsoft Cursor для OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md), которая поддерживает пакетные обновления.  
  
-   Задайте для соединения базу данных по умолчанию со свойством [DefaultDatabase](../../../ado/reference/ado-api/defaultdatabase-property.md) .  
  
-   Установите уровень изоляции для транзакций, открытых в соединении со свойством [IsolationLevel](../../../ado/reference/ado-api/isolationlevel-property.md) .  
  
-   Укажите поставщик OLE DB с помощью свойства [provider](../../../ado/reference/ado-api/provider-property-ado.md) .  
  
-   Установите и попозже приостановить физическое подключение к источнику данных с помощью методов [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) и [Close](../../../ado/reference/ado-api/close-method-ado.md) .  
  
-   Выполните команду в соединении с методом [EXECUTE](../../../ado/reference/ado-api/execute-method-ado-connection.md) и настройте выполнение с помощью свойства [CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md) .  
  
    > [!NOTE]
    >  Чтобы выполнить запрос без использования объекта Command, передайте строку запроса в метод **EXECUTE** объекта **Connection** . Однако объект [команды](../../../ado/reference/ado-api/command-object-ado.md) необходим, если нужно сохранить текст команды и повторно выполнить его, либо использовать параметры запроса.  
  
-   Управление транзакциями в открытом соединении, включая вложенные транзакции, если поставщик поддерживает их, с помощью методов [примеры BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md), [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)и [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) и свойства [Attributes](../../../ado/reference/ado-api/attributes-property-ado.md) .  
  
-   Проверьте ошибки, возвращенные из источника данных с помощью коллекции [ошибок](../../../ado/reference/ado-api/errors-collection-ado.md) .  
  
-   Считывает версию из реализации ADO, используемой со свойством [Version](../../../ado/reference/ado-api/version-property-ado.md) .  
  
-   Получите сведения о схеме базы данных с помощью метода [OpenSchema](../../../ado/reference/ado-api/openschema-method.md) .  
  
 Объекты **соединения** можно создавать независимо от любого другого ранее определенного объекта.  
  
 Можно выполнять именованные команды или хранимые процедуры, как если бы они были собственными методами для объекта **соединения** , как показано в следующем разделе. Если именованная команда имеет то же имя, что и хранимая процедура, то для объекта **соединения** вызовите "собственный вызов метода" всегда выполните именованную команду вместо процедуры Store.  
  
> [!NOTE]
>  Не используйте эту функцию (вызов именованной команды или хранимой процедуры, как если бы он был собственным методом в объекте **Connection** ) в приложении Microsoft® .NET Framework, поскольку базовая реализация функции конфликтует с тем, как .NET Framework взаимодействует с COM.  
  
## <a name="execute-a-command-as-a-native-method-of-a-connection-object"></a>Выполнение команды в качестве собственного метода объекта соединения  
 Чтобы выполнить команду, присвойте команде имя, используя свойство [имя](../../../ado/reference/ado-api/name-property-ado.md) объекта **команды** . Задайте для свойства **ActiveConnection** объекта **Command** значение Connection. Затем выполните инструкцию, где имя команды используется как метод для объекта **соединения** , за которым следуют все параметры и объект **Recordset** , если возвращаются какие-либо строки. Задайте свойства **набора записей** , чтобы настроить результирующий **набор записей**. Пример:  
  
```  
Dim cnn As New ADODB.Connection  
Dim cmd As New ADODB.Command  
Dim rst As New ADODB.Recordset  
...  
cnn.Open "..."  
cmd.Name = "yourCommandName"  
cmd.ActiveConnection = cnn  
...  
'Your command name, any parameters, and an optional Recordset.  
cnn. "parameter", rst  
```  
  
## <a name="execute-a-stored-procedure-as-a-native-method-of-a-connection-object"></a>Выполнение хранимой процедуры в качестве собственного метода объекта соединения  
 Чтобы выполнить хранимую процедуру, выполните инструкцию, где имя хранимой процедуры используется как метод в объекте **Connection** , за которым следуют все параметры. ADO выполнит «наилучшее предположение» типов параметров. Пример:  
  
```  
Dim cnn As New ADODB.Connection  
...  
'Your stored procedure name and any parameters.  
cnn. "parameter"  
```  
  
 Объект **соединения** является надежным для сценариев.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Connection](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Коллекция Errors (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Приложение А. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md)
