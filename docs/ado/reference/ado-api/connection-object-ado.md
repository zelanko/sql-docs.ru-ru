---
title: "Объект соединения (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Connection
helpviewer_keywords:
- Connection object [ADO]
ms.assetid: ef6b1824-5b12-43db-89d7-8f3d13896d4d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: be2ba43e34c56e19dcb6eee03368ab1b3bc442a1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="connection-object-ado"></a>Объект соединения (ADO)
Представляет открытое соединение с источником данных.  
  
## <a name="remarks"></a>Замечания  
 Объект **подключения** представляет уникальный сеанс с источником данных. В системе клиента и сервера базы данных может быть эквивалентно действительное сетевое подключение к серверу. В зависимости от функциональных возможностей, поддерживаемых поставщика, некоторые коллекции, методы или свойства **подключения** могут оказаться недоступными.  
  
 С коллекциями, методы и свойства **подключения** объекта, можно сделать следующее:  
  
-   Настройка подключения, прежде чем открыть его с [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md), [ConnectionTimeout](../../../ado/reference/ado-api/connectiontimeout-property-ado.md), и [режим](../../../ado/reference/ado-api/mode-property-ado.md) свойства. **ConnectionString** — свойство по умолчанию **подключения** объекта.  
  
-   Задать [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойство клиенту для вызова [службы курсора для OLE DB Microsoft](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md), который поддерживает пакетные обновления.  
  
-   Задать базу данных по умолчанию для соединения с [DefaultDatabase](../../../ado/reference/ado-api/defaultdatabase-property.md) свойство.  
  
-   Уровень изоляции транзакций, открытом в соединении с набора [IsolationLevel](../../../ado/reference/ado-api/isolationlevel-property.md) свойство.  
  
-   Укажите поставщика OLE DB с [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство.  
  
-   Установить и позднее прервать физическое соединение с источником данных с [откройте](../../../ado/reference/ado-api/open-method-ado-connection.md) и [закрыть](../../../ado/reference/ado-api/close-method-ado.md) методы.  
  
-   Выполнить команду для соединения с [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) метод и настройте выполнение с [CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md) свойство.  
  
    > [!NOTE]
    >  Чтобы выполнить запрос без использования объект Command, передать строку запроса для **Execute** метод **подключения** объекта. Тем не менее [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта является обязательным, если вы хотите сохранить текст команды и повторно выполните ее или использовать параметры запроса.  
  
-   Управление транзакциями на открытое соединение, включая вложенные транзакции, если поставщик поддерживает, с [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md), [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md), и [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) методы и [атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) свойство.  
  
-   Проанализируйте ошибки, возвращенные из источника данных с [ошибки](../../../ado/reference/ado-api/errors-collection-ado.md) коллекции.  
  
-   Прочитать версию из ADO реализацию, используемую с [версии](../../../ado/reference/ado-api/version-property-ado.md) свойство.  
  
-   Получить данные схемы о базе данных с [OpenSchema](../../../ado/reference/ado-api/openschema-method.md) метод.  
  
 Можно создать **подключения** объектов независимо от любого другого ранее определенного объекта.  
  
 Вы можете выполнить именованных команд или хранимых процедур, как если бы они были собственных методов на **подключения** объекта, как показано в следующем разделе. Когда именованную команду имеет то же имя, что и хранимая процедура, выполнения вызова «собственный метод» на **подключения** объект всегда выполняться именованную команду вместо хранимую процедуру.  
  
> [!NOTE]
>  Не используйте эту функцию (вызов именованную команду или хранимую процедуру, как если бы оно собственного метода на **подключения** объект) в приложении Microsoft® .NET Framework так как базовая реализация конфликты, функция с тем, как .NET Framework взаимодействует с COM.  
  
## <a name="execute-a-command-as-a-native-method-of-a-connection-object"></a>Выполнить команду в качестве собственного метода объекта соединения  
 Для выполнения команды, присвойте команде имя, используя **команда** объекта [имя](../../../ado/reference/ado-api/name-property-ado.md) свойства. Задать **ActiveConnection** свойство **команда** объект соединения. Затем выполните инструкции, где используется имя команды, как если бы это был метод на **подключения** объекта, следуют любые параметры и **набора записей** объекта, если возвращаются все строки. Задать **записей** свойства для настройки результирующего **записей**. Например:  
  
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
  
## <a name="execute-a-stored-procedure-as-a-native-method-of-a-connection-object"></a>Выполнение хранимой процедуры как собственный метод объекта соединения  
 Для выполнения хранимой процедуры, выполните инструкции, где используется имя хранимой процедуры, как если бы это был метод на **подключения** объекта, следуют любые параметры. ADO сделает «наиболее подходящие» типы параметров. Например:  
  
```  
Dim cnn As New ADODB.Connection  
...  
'Your stored procedure name and any parameters.  
cnn. "parameter"  
```  
  
 **Подключения** объекта безопасные для использования.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства объекта соединения, методы и события](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Объект команды (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Коллекция ошибок (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Коллекция свойств (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Поставщики приложение A:](../../../ado/guide/appendixes/appendix-a-providers.md)

