---
title: "Сохранение данных | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: 21c162ca-2845-4dd8-a49d-e715aba8c461
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ecda57863abf45f1256f192d933c99bfb09a67dd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="persisting-data"></a>Сохранение данных
Портативные компьютеры (например, с помощью ноутбуков) создал потребность в приложениях, которые могут выполняться в подключенном и отключенном состоянии. ADO добавлена поддержка это, предоставляя возможность сохранения клиентских курсоров разработчик **записей** на диск и перезагрузить его позже.  
  
 Существует несколько сценариев, в которых можно использовать этот тип функции, включая следующие:  
  
-   **Проходящих:** при извлечении приложения в дороге, крайне важно предоставить возможность вносить изменения и добавления новых записей, которые затем можно использовать подключение к базе данных более поздней версии и были зафиксированы.  
  
-   **Уточняющие запросы, обновляемые сравнительно редко:** часто в приложении используются таблицы в качестве уточняющих запросов, например, состояния таблиц налогов. Они обновляются нечасто и доступны только для чтения. Вместо повторного считывания эти данные с сервера при каждом запуске приложения, приложения можно просто загрузить данные из локально материализованный **записей**.  
  
 В ADO для сохранения и загрузки **наборы записей**, используйте **Recordset.Save** и **Recordset.Open(,,,adCmdFile)** методы ADO **записей**объекта.  
  
 Можно использовать **сохранить набор записей** метод для сохранения вашей ADO **записей** в файл на диске. (Можно также сохранить **записей** для ADO **поток** объекта. **Поток** объекты описаны далее в этом руководстве.) Позже, можно использовать **откройте** метод, чтобы снова открыть **записей** когда вы будете готовы для использования. По умолчанию сохраняет ADO **записей** в собственный формат TableGram дополнительные данные (ADTG). Этот двоичный формат задается с помощью **adPersistADTG PersistFormatEnum** значение. Кроме того, вы можете сохранить ваш **записей** ожидания в виде XML с использованием **adPersistXML**. Дополнительные сведения о сохранении наборы записей в формате XML см. в разделе [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md).  
  
 Синтаксис **Сохранить** метод является следующим образом:  
  
```  
  
recordset.  
Save  
Destination, PersistFormat  
  
```  
  
 При первом сохранении **записей**, это необязательно для указания *назначения*. Если не указан *назначения*, будет создан новый файл с именем, заданным равным [источника](../../../ado/reference/ado-api/source-property-ado-recordset.md) свойство **набора записей**.  
  
 Пропустить *назначения* при последующем вызове **Сохранить** после первого сохранения или ошибку во время выполнения возникнет. Если впоследствии вызвать **Сохранить** с новым *назначения*, **набора записей** сохраняется в новое место назначения. Тем не менее, новое назначение и исходное расположение будет быть открытым.  
  
 **Сохранить** не закрывает **записей** или *назначения*, поэтому можно продолжать работать с **записей** и сохраните изменения. *Назначение* остается открытым до **записей** закрыт, во время которого можно читать другие приложения, но не запись *назначения*.  
  
 По причинам безопасности **Сохранить** метод допускает использование только настройки безопасности низким и пользовательский сценарий, выполняемый обозревателем Microsoft Internet Explorer.  
  
 Если **Сохранить** при асинхронном вызове метода **записей** выборки, выполнение или обновление операция выполняется **Сохранить** ожидает, пока асинхронная операция Завершите.  
  
 Записи сохраняются, начиная с первой строки **записей**. Когда **Сохранить** метод завершения, текущее положение строки перемещается в первой строке **записей**.  
  
 Для получения наилучших результатов установите [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойства **adUseClient** с **Сохранить**. Если поставщик не поддерживает все функциональные возможности, необходимые для сохранения **записей** объектов, функция будет доступна службе курсора.  
  
 При **записей** сохраняется вместе с **CursorLocation** свойство **adUseServer**, возможность обновления для **записей**ограничено. Как правило только для одной таблицы обновления, вставки и удаления разрешены (зависят от поставщика функциональных возможностей). [Resync](../../../ado/reference/ado-api/resync-method.md) также метод недоступен в этой конфигурации.  
  
 Поскольку *назначения* параметр принимает любой объект, поддерживающий OLE DB **IStream** интерфейса, можно сохранить **записей** непосредственно к ASP  **Ответ** объекта.  
  
 В следующем примере **Сохранить** и **откройте** методы используются для сохранения **записей** и открыть позднее:  
  
```  
'BeginPersist  
   conn.ConnectionString = _  
   "Provider=SQLOLEDB;Data Source=MySQLServer;" _  
      & "Integrated Security=SSPI;Initial Catalog=pubs"  
   conn.Open  
  
   conn.Execute "create table testtable (dbkey int " & _  
      "primary key, field1 char(10))"  
   conn.Execute "insert into testtable values (1, 'string1')"  
  
   Set rst.ActiveConnection = conn  
   rst.CursorLocation = adUseClient  
  
   rst.Open "select * from testtable", conn, adOpenStatic, _  
      adLockBatchOptimistic  
  
   'Change the row on the client  
   rst!field1 = "NewValue"  
  
   'Save to a file--the .dat extension is an example; choose  
   'your own extension. The changes will be saved in the file  
   'as well as the original data.  
   MyFile = Dir("c:\temp\temptbl.dat")  
   If MyFile <> "" Then  
       Kill "c:\temp\temptbl.dat"  
   End If  
  
   rst.Save "c:\temp\temptbl.dat", adPersistADTG  
   Set rst = Nothing  
  
   'Now reload the data from the file  
   Set rst = New ADODB.Recordset  
   rst.Open "c:\temp\temptbl.dat", , adOpenStatic, _  
      adLockBatchOptimistic, adCmdFile  
  
   Debug.Print "After Loading the file from disk"  
   Debug.Print "   Current Edited Value: " & rst!field1.Value  
   Debug.Print "   Value Before Editing: " & rst!field1.OriginalValue  
  
   'Note that you can reconnect to a connection and  
   'submit the changes to the data source  
   Set rst.ActiveConnection = conn  
   rst.UpdateBatch  
'EndPersist  
```  
  
## <a name="remarks"></a>Замечания  
 Этот раздел содержит следующие подразделы.  
  
-   [Дополнительные сведения о сохраняемости набора записей](../../../ado/guide/data/more-about-recordset-persistence.md)  
  
-   [Сохранение отфильтрованных и иерархических наборов записей](../../../ado/guide/data/persisting-filtered-and-hierarchical-recordsets.md)  
  
-   [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
