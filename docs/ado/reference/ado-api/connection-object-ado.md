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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 278e2d90ed20b99706f00acf72e2892941c42865
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67933566"
---
# <a name="connection-object-ado"></a>Объект Connection (ADO)
Представляет открытое подключение к источнику данных.  
  
## <a name="remarks"></a>Примечания  
 Объект **подключения** представляет уникальный сеанс с источником данных. В системе базы данных клиент/сервер может быть эквивалентно действительное сетевое подключение к серверу. В зависимости от функциональных возможностей, поддерживаемых поставщиком, некоторые коллекции, методы или свойства **подключения** могут оказаться недоступными.  
  
 С помощью коллекций, методы и свойства **подключения** объекта, можно сделать следующее:  
  
-   Настройка подключения перед его с открытием [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md), [ConnectionTimeout](../../../ado/reference/ado-api/connectiontimeout-property-ado.md), и [режим](../../../ado/reference/ado-api/mode-property-ado.md) свойства. **ConnectionString** — свойство по умолчанию **подключения** объекта.  
  
-   Задайте [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойство клиенту для вызова [служба курсора Майкрософт для OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md), который поддерживает пакетные обновления.  
  
-   Задайте базу данных по умолчанию для соединения с [DefaultDatabase](../../../ado/reference/ado-api/defaultdatabase-property.md) свойство.  
  
-   Уровень изоляции для транзакций, открытом в соединении с набора [IsolationLevel](../../../ado/reference/ado-api/isolationlevel-property.md) свойство.  
  
-   Укажите поставщика OLE DB с помощью [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство.  
  
-   Установите, а позже прервать физическое подключение к источнику данных с помощью [откройте](../../../ado/reference/ado-api/open-method-ado-connection.md) и [закрыть](../../../ado/reference/ado-api/close-method-ado.md) методы.  
  
-   Выполнить команду для соединения с [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) метод и настройте выполнение с [CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md) свойство.  
  
    > [!NOTE]
    >  Чтобы выполнить запрос без использования объект Command, передать строку запроса для **Execute** метод **подключения** объекта. Тем не менее [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта является обязательным, если вы хотите сохранить текст команды и повторно выполните ее или использовать параметры запроса.  
  
-   Управление транзакциями на открытое соединение, включая вложенные транзакции, если поставщик поддерживает, с помощью [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md), [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md), и [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) методы и [атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) свойство.  
  
-   Проанализируйте ошибки, возвращенные из источника данных с помощью [ошибки](../../../ado/reference/ado-api/errors-collection-ado.md) коллекции.  
  
-   Прочитать версию из ADO реализацию, используемую с [версии](../../../ado/reference/ado-api/version-property-ado.md) свойство.  
  
-   Получение сведений о схеме о базе данных с помощью [OpenSchema](../../../ado/reference/ado-api/openschema-method.md) метод.  
  
 Можно создать **подключения** объектов независимо от любого другого ранее определенного объекта.  
  
 Вы можете выполнить именованные команды или хранимых процедур, как если бы они находились собственных методов в **подключения** объекта, как показано в следующем разделе. Если команду с именем имеет то же имя, что хранимые процедуры, вызова неуправляемого кода «собственный метод» на **подключения** объект всегда выполнить команду с именем, а не хранимой процедуры.  
  
> [!NOTE]
>  Не используйте эту функцию (вызов именованную команду или хранимую процедуру, как будто собственного метода на **подключения** объекта) в приложении Microsoft® .NET Framework, так как базовая реализация того, функция конфликты с тем, как .NET Framework взаимодействует с COM.  
  
## <a name="execute-a-command-as-a-native-method-of-a-connection-object"></a>Выполнение команды как собственный метод объекта подключения  
 Для выполнения команды, присвойте команде имя, используя **команда** объект [имя](../../../ado/reference/ado-api/name-property-ado.md) свойство. Задайте **ActiveConnection** свойство **команда** объект соединения. Затем предстоит выполнить инструкцию, где используется имя команды, как если бы он был методом на **подключения** объекта, а затем все параметры и **набор записей** объекта, если возвращаются все строки. Задайте **записей** свойства для настройки результирующего **записей**. Пример:  
  
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
  
## <a name="execute-a-stored-procedure-as-a-native-method-of-a-connection-object"></a>Выполнение хранимой процедуры в качестве собственного метода объекта подключения  
 Для выполнения хранимой процедуры, выполнить инструкцию, где используется имя хранимой процедуры, как если бы он был методом на **подключения** объекта, а затем все параметры. ADO сделает «наиболее подходящих значений» типов параметров. Пример:  
  
```  
Dim cnn As New ADODB.Connection  
...  
'Your stored procedure name and any parameters.  
cnn. "parameter"  
```  
  
 **Подключения** объект безопасен для скриптов.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства объекта соединения, методы и события](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Коллекция Errors (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Приложение а. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md)
