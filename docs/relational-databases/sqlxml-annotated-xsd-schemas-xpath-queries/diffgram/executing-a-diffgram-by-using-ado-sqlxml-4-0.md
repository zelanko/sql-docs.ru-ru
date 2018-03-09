---
title: "Выполнение дельты с использованием ADO (SQLXML 4.0) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], SQLOLEDB Provider
- ADO [SQLXML]
- SQLXMLOLEDB Provider, DiffGrams
- data providers [SQLXML], SQLOLEDB Provider
- DiffGrams [SQLXML], ADO
ms.assetid: 741fce82-de83-4923-86eb-30acb5b9a5e6
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f3baa16c0f283e8066a764801f31422c6c2eb8f7
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="executing-a-diffgram-by-using-ado-sqlxml-40"></a>Выполнение дельты с использованием ADO (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Следующее приложение на языке [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic использует ADO для установки соединения с экземпляром Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и выполняет DiffGram. В этом приложении дельты и схема XSD хранятся в файле. Приложение загружает DiffGram из заданного файла. Можно использовать любые дельты (и связанной схемы XSD) описано в [примеры дельт](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).  
  
 Ниже приводится последовательность действий в образце приложения.  
  
-   **Conn** объекта (**ADODB. Подключение**) устанавливает подключение к запущенному экземпляру SQL Server, на конкретном сервере.  
  
-   **Cmd** объекта (**ADODB.Command**) выполняется в рамках установленного подключения.  
  
-   В качестве диалекта команды задано значение DBGUID_MSSQLXML.  
  
-   Дельта копируется в поток команды (**strmIn**) из файла.  
  
-   Выходной поток команды задано значение **StrmOut** объекта (**ADODB. Поток**) который получает все возвращенные данные.  
  
-   При использовании поставщика SQLOLEDB вы по умолчанию получаете функциональность Microsoft SQLXML, предоставляемую библиотекой Sqlxmlx.dll. Чтобы использовать библиотеку Sqlxml4.dll с поставщиком SQLOLEDB **версии SQLXML** свойству необходимо присвоить значение **SQLXML.4.0** на поставщик SQLOLEDB **подключения** объекта.  
  
-   Команда (дельта) будет выполнена.  
  
 Следующий код представляет собой образец приложения.  
  
> [!NOTE]  
>  В коде необходимо задать имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в строке соединения.  
  
```  
Private Sub Command1_Click()  
  Dim cmd As New ADODB.Command  
  Dim conn As New ADODB.Connection  
  Dim strmOut As New ADODB.Stream  
  Dim strmIn As New ADODB.Stream  
  
  'Open a connection to SQL Server.  
  conn.Provider = "SQLOLEDB"  
  conn.Open "server=SqlServerName; database=tempdb; Integrated Security=SSPI; "  
  conn.Properties("SQLXML Version") = "SQLXML.4.0"  
  Set cmd.ActiveConnection = conn  
  strmIn.Open  
  strmIn.Charset = "UTF-8"  
  strmIn.LoadFromFile "C:\SomeFilePath\SampleDiffGram.xml"  
  strmIn.Position = 0  
  Set cmd.CommandStream = strmIn  
  
  strmOut.Open  
  cmd.Properties("Output Stream").Value = strmOut  
  cmd.Properties("Output Encoding").Value = "UTF-8"  
  
  cmd.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  cmd.Properties("Mapping Schema") = "C:\SomeFilePath\SampleDiffGram.xml"  
  cmd.Execute , , adExecuteStream  
  strmOut.Position = 0  
  Set cmd = Nothing  
  strmOut.Charset = "UTF-8"  
  strmOut.SaveToFile "C:\DropIt.txt", adSaveCreateOverWrite  
  strmOut.Close  
  Set strmOut = Nothing  
  
End Sub  
```  
  
### <a name="to-test-the-diffgram"></a>Проверка дельты  
  
1.  В папку на компьютере, скопируйте любой дельту и соответствующую схему XSD из одного из примеров в [примеры дельт](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).  
  
2.  Откройте Visual Basic и создайте проект стандартного исполняемого файла.  
  
3.  Добавьте эти ссылки в проект:  
  
    ```  
    Microsoft ActiveX Data Objects 2.8 Library  
    ```  
  
4.  На панели инструментов нажмите кнопку **CommandButton**, а затем перетащите кнопку на форму.  
  
5.  Дважды нажмите кнопку, чтобы изменить ее код, и добавьте код приложения из раздела.  
  
6.  Отредактируйте код, чтобы в нем указывались имена файлов DiffGram и XSD. Также отредактируйте строку соединения.  
  
7.  Запустите приложение. Результат выполнения зависит от типа DiffGram.  
  
  
