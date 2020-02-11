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
ms.openlocfilehash: 63323fd8ed18f57a68633dce0525d1d37e4978ae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924705"
---
# <a name="persisting-data"></a>Сохранение данных
Переносные вычисления (например, использование ноутбуков) создавали потребность в приложениях, которые могут работать как в подключенном, так и в отключенном состоянии. В ADO добавлена поддержка, позволяющая разработчику сохранить **набор записей** клиентского курсора на диск и перезагрузить его позже.  
  
 Существует несколько сценариев, в которых можно использовать этот тип функции, включая следующие:  
  
-   **Путешествие:** При получении приложения в дороге крайне важно предоставить возможность вносить изменения и добавлять новые записи, которые затем могут быть повторно подключены к базе данных позже и зафиксированы.  
  
-   **Нечасто обновляемые уточняющие запросы:** Часто в приложении таблицы используются как уточняющие запросы, например таблицы штатных налогов. Они обновляются редко и доступны только для чтения. Вместо повторного считывания этих данных с сервера при каждом запуске приложения приложение может просто загрузить данные из локально сохраненного **набора записей**.  
  
 В ADO для сохранения и загрузки **наборов записей**используются методы **Recordset. Save** и **Recordset. Open (,,,, Адкмдфиле)** в объекте **набора записей** ADO.  
  
 Для сохранения **набора записей** ADO в файл на диске можно использовать метод **Save набора записей** . (Можно также сохранить **набор записей** в объект **потока** ADO. Объекты **потока** обсуждаются далее в этом руководством.) Позднее можно использовать метод **Open** , чтобы повторно открыть **набор записей** , когда вы будете готовы использовать его. По умолчанию ADO сохраняет **набор записей** в собственном формате Microsoft Advanced Data ТАБЛЕГРАМ (адтг). Этот двоичный формат указывается с помощью значения **Персистформатенум адперсистадтг** . Кроме того, можно сохранить **набор записей** в формате XML с помощью **адперсистксмл**. Дополнительные сведения о сохранении наборов записей в виде XML см. [в разделе Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md).  
  
 Синтаксис метода **Save** выглядит следующим образом:  
  
```  
  
recordset.  
Save  
Destination, PersistFormat  
  
```  
  
 При первом сохранении **набора записей**необязательно указывать *назначение*. Если опустить *назначение*, будет создан новый файл с именем, равным значению свойства [Source](../../../ado/reference/ado-api/source-property-ado-recordset.md) **набора записей**.  
  
 Опустить *назначение* при последующем вызове **Save** после первого сохранения или ошибки времени выполнения. При последующем вызове метода **Save** с *новым назначением* **набор записей** сохраняется в новом месте назначения. Однако новое назначение и исходное место назначения будут открыты.  
  
 При **сохранении** не закрывается **набор записей** или *назначение*, поэтому можно продолжить работу с **набором записей** и сохранить последние изменения. *Назначение* остается открытым до тех пор, пока **набор записей** не будет закрыт, в то время как другие приложения смогут считывать, но не могут записывать в *место назначения*.  
  
 По соображениям безопасности метод **Save** позволяет использовать только низкий и пользовательский параметры безопасности из сценария, выполняемого Microsoft Internet Explorer.  
  
 Если метод **Save** вызывается во время выполнения асинхронной операции выборки, выполнения или обновления **набора записей** , **Сохраните** ожидание до завершения асинхронной операции.  
  
 Записи сохраняются, начиная с первой строки **набора записей**. По завершении метода **Save** текущее расположение строки перемещается в первую строку **набора записей**.  
  
 Для получения наилучших результатов задайте для свойства [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) значение **адусеклиент** с параметром **Save**. Если поставщик не поддерживает все функции, необходимые для сохранения объектов **набора записей** , Служба курсора предоставит эту функцию.  
  
 Если **набор записей** сохраняется с помощью свойства **CursorLocation** , установленного в значение **Адусесервер**, возможность обновления для **набора записей** ограничена. Как правило, разрешены только обновления, вставки и удаления в одной таблице (зависит от функциональности поставщика). Метод повторной [синхронизации](../../../ado/reference/ado-api/resync-method.md) также недоступен в этой конфигурации.  
  
 Так как параметр *назначения* может принимать любой объект, поддерживающий интерфейс OLE DB **IStream** , **набор записей** можно сохранить непосредственно в объекте **ответа** ASP.  
  
 В следующем примере методы **Save** и **Open** используются для сохранения **набора записей** и последующего повторного открытия.  
  
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
  
## <a name="remarks"></a>Remarks  
 Этот раздел содержит следующие подразделы.  
  
-   [Дополнительные сведения о сохраняемости набора записей](../../../ado/guide/data/more-about-recordset-persistence.md)  
  
-   [Сохранение отфильтрованных и иерархических наборов записей](../../../ado/guide/data/persisting-filtered-and-hierarchical-recordsets.md)  
  
-   [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
