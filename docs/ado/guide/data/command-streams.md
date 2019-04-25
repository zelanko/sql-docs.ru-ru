---
title: Команда потоков | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- command streams [ADO]
- streams [ADO], command
ms.assetid: 0ac09dbe-2665-411e-8fbb-d1efe6c777be
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6a5e9581a2a236eab869e74825ee97e7e289d44
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472700"
---
# <a name="command-streams"></a>Потоки команд
ADO всегда поддерживал вход команды в строковом формате, определяемое **CommandText** свойство. Кроме того, с помощью ADO 2.7 или более поздней версии, также можно потока данных для ввода команды путем назначения потока **CommandStream** свойство. Вы можете назначить ADO **Stream** объекта или любым объектом, поддерживающим COM **IStream** интерфейс.  
  
 Содержимое в поток команды просто передается от ADO к поставщику, поэтому поставщик должен поддерживать вход команды потоком для работы этой функции. Например SQL Server поддерживает запросы в виде XML-шаблоны или расширения OpenXML Transact-SQL.  
  
 Поскольку сведения о потоке должен интерпретироваться поставщиком, необходимо указать в качестве диалекта команды, задав **диалект** свойство. Значение **диалект** является строка, содержащая GUID, определенный поставщиком. Сведения о допустимых значениях для **диалект** поддерживается поставщиком, см. в документации поставщика.  
  
## <a name="xml-template-query-example"></a>Пример запроса XML-файла шаблона  
 Следующий пример написан на языке VBScript в базу данных "Борей".  
  
 Во-первых, инициализации и запуска **Stream** объект, который будет использоваться для хранения потока запроса:  
  
```  
Dim adoStreamQuery  
Set adoStreamQuery = Server.CreateObject("ADODB.Stream")  
adoStreamQuery.Open  
```  
  
 Содержимое потока запроса будет шаблон XML-запрос.  
  
 Шаблон запроса требует наличия ссылок на пространства имен XML с sql: префикс \<sql:query > тег. Инструкцию SQL SELECT включены как содержимое XML-шаблон и назначить строковой переменной, следующим образом:  
  
```  
sQuery = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'>  
<sql:query> SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME </sql:query>  
</ROOT>"  
```  
  
 Запишите строку в поток:  
  
```  
adoStreamQuery.WriteText sQuery, adWriteChar  
adoStreamQuery.Position = 0  
```  
  
 Назначить adoStreamQuery для **CommandStream** свойство объекта ADO **команда** объекта:  
  
```  
Dim adoCmd  
Set adoCmd  = Server.CreateObject("ADODB.Command"")  
adoCmd.CommandStream = adoStreamQuery  
```  
  
 Укажите командный язык **диалект**, которое указывает, как SQL Server поставщик OLE DB должны интерпретировать поток команды. Диалект, указанный GUID поставщика:  
  
```  
adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"  
```  
  
 Наконец, выполните запрос и возвращают результаты **записей** объекта:  
  
```  
Set objRS = adoCmd.Execute  
```
