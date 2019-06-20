---
title: Сохранение данных | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: 21c162ca-2845-4dd8-a49d-e715aba8c461
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0f2d47229b7383c11740ca3d7a20ad8e420931a5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700473"
---
# <a name="persisting-data"></a>Сохранение данных
Портативные компьютеры (например, используя переносные компьютеры), создала потребность в приложения, работающие в подключенном и автономном состоянии. ADO имеет дополнительную поддержку для этого, предоставляя разработчику возможность сохранения клиентский курсор **записей** на диск и перезагрузить его позже.  
  
 Существует несколько сценариев, в которых можно использовать этот тип функции, включая следующие:  
  
-   **Поездок:** При создании приложения в дороге, крайне важно предоставить возможность вносить изменения и добавления новых записей, которые затем можно использовать подключение к базе данных более поздней версии и фиксации.  
  
-   **Обновляются редко уточняющие запросы:** Часто в приложении, таблицы используются как уточняющие запросы — например, состояние таблиц налогов. Они обновляются нечасто и доступны только для чтения. Вместо повторного чтения этих данных с сервера при каждом запуске приложения, приложение может просто загрузить данные из локально сохраненного **записей**.  
  
 В ADO для сохранения и загрузки **наборы записей**, использовать **Recordset.Save** и **Recordset.Open(,,,adCmdFile)** методы ADO **записей**объекта.  
  
 Можно использовать **сохранить набор записей** метод для сохранения в ADO **записей** в файл на диске. (Вы также можете сохранить **записей** для ADO **Stream** объекта. **Stream** объекты рассматриваются далее в этом руководстве.) Затем, с помощью **откройте** метод, чтобы снова открыть **набор записей** когда вы будете готовы использовать его. По умолчанию сохраняет ADO **записей** в собственный формат TableGram дополнительные данные (ADTG). Этот двоичный файл задается с помощью **adPersistADTG PersistFormatEnum** значение. Кроме того, вы можете сохранить ваши **записей** как XML с использованием **adPersistXML**. Дополнительные сведения о сохранении наборы записей в формате XML, см. в разделе [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md).  
  
 Синтаксис **Сохранить** метод выглядит следующим образом:  
  
```  
  
recordset.  
Save  
Destination, PersistFormat  
  
```  
  
 При первом сохранении **записей**, она необязательна для указания *назначения*. Если опустить *назначения*, будет создан новый файл с именем присвоено значение [источника](../../../ado/reference/ado-api/source-property-ado-recordset.md) свойство **записей**.  
  
 Опустить *назначения* при последующем вызове **Сохранить** после первого сохранения или ошибка времени выполнения будет выполняться. Если после этого вызвать **Сохранить** с новым *назначения*, **записей** сохраняется новое место назначения. Тем не менее новое место назначения и исходное расположение оба будут открыты.  
  
 **Сохранить** не закрывает **записей** или *назначения*, поэтому можно продолжать работать с **записей** и сохраните изменения. *Назначение* остается открытым, пока **записей** закрыто, во время которого можно читать другие приложения, но не запись *назначения*.  
  
 По соображениям безопасности **Сохранить** метод позволяет только использовать настройки безопасности низким и пользовательский сценарий, выполняемый обозревателем Microsoft Internet Explorer.  
  
 Если **Сохранить** при асинхронном вызове метода **записей** выборки, выполнение или обновление выполняется операция, **Сохранить** ожидает, пока не асинхронной операции Завершите.  
  
 Записи сохраняются, начиная с первой строки **записей**. Когда **Сохранить** метод закончит работу, текущая позиция строки перемещается к первой строке **записей**.  
  
 Для получения наилучших результатов установите [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойства **adUseClient** с **Сохранить**. Если ваш поставщик не поддерживает все функциональные возможности, необходимые для сохранения **записей** объектов, функция будет доступна служба курсора.  
  
 При **записей** сохраняемое **CursorLocation** свойство значение **adUseServer**, возможности обновления для **записей**ограничено. Как правило только для одной таблицы обновления, вставки и удаления разрешены (в зависимости от функциональные возможности поставщика). [Resync](../../../ado/reference/ado-api/resync-method.md) также метод недоступен в этой конфигурации.  
  
 Так как *назначения* параметр может принимать любой объект, который поддерживает объект OLE DB **IStream** интерфейс, вы можете сохранить **записей** непосредственно к ASP  **Ответ** объекта.  
  
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
  
## <a name="remarks"></a>Примечания  
 Этот раздел содержит следующие подразделы.  
  
-   [Дополнительные сведения о сохраняемости набора записей](../../../ado/guide/data/more-about-recordset-persistence.md)  
  
-   [Сохранение отфильтрованных и иерархических наборов записей](../../../ado/guide/data/persisting-filtered-and-hierarchical-recordsets.md)  
  
-   [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
