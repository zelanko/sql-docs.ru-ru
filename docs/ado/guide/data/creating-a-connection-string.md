---
title: Создание строки подключения | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
- connection strings [ADO]
ms.assetid: 14eae122-2d1e-40c8-b88e-b7cb8dfbc93b
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc700bdc0006a4591e61e15f2796b73c194dc5a1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="creating-a-connection-string"></a>Создание строки подключения
Строка подключения состоит из списка пар аргументов и значений (параметров), разделенных точкой с запятой. Например:  
  
```  
"arg1=val1; arg2=val2; ... argN=valN;"  
```  
  
 Все параметры должны распознаваться ADO или указанного поставщика.  
  
 ADO распознает следующие пять аргументов в строке подключения.  
  
|Аргумент|Описание|  
|--------------|-----------------|  
|*Поставщик*|Задает имя поставщика, который используется для подключения.|  
|*Имя файла*|Указывает имя файла поставщика (например, объект источника материализованных данных), содержащий сведения о подключении предустановки.|  
|*URL-адрес*|Указывает строку подключения, как абсолютный URL-адрес, идентифицирующий ресурса, например файла или каталога.|  
|*Удаленный поставщик*|Задает имя поставщика, который используется при открытии клиентского соединения. (Удаленный канал передачи данных только.)|  
|*Удаленный сервер*|Задает имя пути сервера для использования при открытии клиентского соединения. (Удаленный канал передачи данных только.)|  
  
 Остальные аргументы передаются поставщику с именем в *поставщика* аргумент, без какой-либо обработки, ADO.  
  
 Приложения HelloData в [HelloData: простое приложение ADO](../../../ado/guide/data/hellodata-a-simple-ado-application.md) используется следующая строка подключения:  
  
```  
m_sConnStr = "Provider=SQLOLEDB;Data Source=MySqlServer;" & _  
             "Initial Catalog=Northwind;Integrated Security='SSPI';"  
```  
  
 В этой строке подключения ADO распознает только `"Provider=SQLOLEDB"` параметр, который задает поставщик Microsoft OLE DB для SQL Server в качестве источника данных ADO. Остальная часть пары аргумент значение, `"Data Source=MySqlServer; Initial Catalog=Northwind;Integrated Security='SSPI';"`, передаются verbatim для данного поставщика. Тип и допустимость такие параметры зависят от поставщика. Сведения о допустимых параметрах, которые могут быть переданы в строке подключения отдельный поставщик документации.  
  
 Согласно поставщик OLE DB для документации по SQL Server, можно заменить «Server» для *источника данных* параметр и «Базы данных» для *Initial Catalog* параметра. Таким образом следующая строка подключения, получились бы идентичен приведенному выше результаты:  
  
```  
m_sConnStr = "Provider=SQLOLEDB;Server=MySqlServer;" & _  
             "Database=Northwind;Integrated Security='SSPI';"  
```
