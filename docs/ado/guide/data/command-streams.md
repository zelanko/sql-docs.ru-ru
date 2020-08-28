---
description: Потоки команд
title: Потоки команд | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- command streams [ADO]
- streams [ADO], command
ms.assetid: 0ac09dbe-2665-411e-8fbb-d1efe6c777be
author: rothja
ms.author: jroth
ms.openlocfilehash: 2ae54835836fecdfbf3b026fe9e6a701a5602d3d
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991545"
---
# <a name="command-streams"></a>Потоки команд
ADO всегда поддерживал ввод команды в строковом формате, указанном свойством **CommandText** . В качестве альтернативы с помощью ADO 2,7 или более поздней версии можно также использовать поток данных для ввода команды, назначив поток свойству **CommandStream** . Можно назначить объект **потока** ADO или любой объект, поддерживающий интерфейс **IStream** com.  
  
 Содержимое потока команд просто передается из ADO поставщику, поэтому поставщик должен поддерживать входные данные команды потоком, чтобы эта функция работала. Например, SQL Server поддерживает запросы в виде XML-шаблонов или расширений OpenXML в Transact-SQL.  
  
 Поскольку сведения о потоке должны интерпретироваться поставщиком, необходимо указать диалект команды, задав свойство **диалект** . Значение **диалекта** — это строка, содержащая идентификатор GUID, который определяется поставщиком. Сведения о допустимых значениях для **диалектов** , поддерживаемых поставщиком, см. в документации поставщика.  
  
## <a name="xml-template-query-example"></a>Пример запроса к шаблону XML  
 Следующий пример написан на языке VBScript в базе данных Northwind.  
  
 Сначала инициализируйте и откройте объект **Stream** , который будет использоваться для хранения потока запросов:  
  
```  
Dim adoStreamQuery  
Set adoStreamQuery = Server.CreateObject("ADODB.Stream")  
adoStreamQuery.Open  
```  
  
 Содержимым потока запросов будет XML-запрос шаблона.  
  
 Для запроса шаблона требуется ссылка на пространство имен XML, определяемое префиксом SQL: \<sql:query> тега. Инструкция SQL SELECT включается в качестве содержимого XML-шаблона и присваивается строковой переменной следующим образом:  
  
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
  
 Назначьте Адостреамкуери свойству **CommandStream** объекта **команды** ADO:  
  
```  
Dim adoCmd  
Set adoCmd  = Server.CreateObject("ADODB.Command"")  
adoCmd.CommandStream = adoStreamQuery  
```  
  
 Укажите **диалект**языка команд, который указывает, как поставщик OLE DB SQL Server должен интерпретировать поток команд. Диалект, заданный идентификатором GUID, зависящим от поставщика:  
  
```  
adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"  
```  
  
 Наконец, выполните запрос и верните результаты в объект **Recordset** :  
  
```  
Set objRS = adoCmd.Execute  
```
