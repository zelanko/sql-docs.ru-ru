---
title: Команда потоки | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- command streams [ADO]
- streams [ADO], command
ms.assetid: 0ac09dbe-2665-411e-8fbb-d1efe6c777be
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 47908910561d4f25ed7b958b9b100f86d5465748
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="command-streams"></a>Команда потоков
ADO всегда поддерживается ввода команды в строку формата, заданного в **CommandText** свойство. Кроме того, при использовании ADO 2.7 или более поздней версии, также можно потока данных для ввода команды путем назначения потока **CommandStream** свойство. Можно назначить ADO **поток** объекта или любым объектом, поддерживающим COM **IStream** интерфейса.  
  
 Содержимого потока команды просто передается от ADO с поставщиком, поэтому поставщик должен поддерживать ввода команды потоком для работы этой функции. Например SQL Server поддерживает запросы в виде XML-шаблоны или расширения OpenXML языка Transact-SQL.  
  
 Поскольку сведения о потоке, должна интерпретироваться поставщиком, необходимо указать диалект команды, задав **диалект** свойство. Значение **диалект** является строка, содержащая GUID, который определяется поставщиком. Дополнительные сведения о допустимых значениях для **диалект** поддерживается поставщиком, обратитесь к документации поставщика.  
  
## <a name="xml-template-query-example"></a>Пример запросов XML-файла шаблона  
 Следующий пример написан на языке VBScript в базу данных "Борей".  
  
 Во-первых, инициализации и запуска **поток** объект, который будет использоваться для хранения в поток запроса:  
  
```  
Dim adoStreamQuery  
Set adoStreamQuery = Server.CreateObject("ADODB.Stream")  
adoStreamQuery.Open  
```  
  
 Содержимое потока запроса будет шаблона XML-запрос.  
  
 Шаблон запроса требует ссылки на пространства имен XML с sql: префикс \<sql:query > тег. Инструкции SQL SELECT включается как содержимое XML-шаблон и присваивается переменной строки следующим образом:  
  
```  
sQuery = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'>  
<sql:query> SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME </sql:query>  
</ROOT>"  
```  
  
 Затем напишите строку в поток:  
  
```  
adoStreamQuery.WriteText sQuery, adWriteChar  
adoStreamQuery.Position = 0  
```  
  
 Назначьте adoStreamQuery для **CommandStream** свойство ADO **команда** объекта:  
  
```  
Dim adoCmd  
Set adoCmd  = Server.CreateObject("ADODB.Command"")  
adoCmd.CommandStream = adoStreamQuery  
```  
  
 Укажите командный язык **диалект**, которое указывает, как интерпретировать поток команды SQL Server поставщик OLE DB. Диалект, указанный GUID поставщика:  
  
```  
adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"  
```  
  
 Наконец, выполните запрос и возвращают результаты **записей** объекта:  
  
```  
Set objRS = adoCmd.Execute  
```
