---
title: Создание строки подключения | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/20/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
- connection strings [ADO]
ms.assetid: 14eae122-2d1e-40c8-b88e-b7cb8dfbc93b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 455fe1c3f5a19b498730909f1c56bf98b03ae51b
ms.sourcegitcommit: e9fcd10c7eb87a4f09ac2d8f7647018e83a5f5c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57972773"
---
# <a name="creating-a-connection-string"></a>Создание строки подключения
Строка подключения состоит из списка пар аргумент значение (то есть параметров), разделенных точкой с запятой. Пример:  
  
```syntax
"arg1=val1; arg2=val2; ... argN=valN;"  
```  
  
 Все параметры должны распознаваться ADO или указанного поставщика.  
  
 ADO распознает следующие пять аргументов в строку подключения.  
  
|Аргумент|Описание|  
|--------------|-----------------|  
|*Поставщик*|Указывает имя поставщика, который используется для подключения.|  
|*Имя файла*|Указывает имя файла поставщика (например, объект источника материализованных данных), содержащий сведения о подключении предустановки.|  
|*URL-адрес*|Задает строку подключения как абсолютный URL-адрес, идентифицирующий ресурс, например файла или каталога.|  
|*Удаленный поставщик*|Указывает имя поставщика, который используется при открытии клиентского соединения. (Удаленные данные только для службы.)|  
|*Удаленный сервер*|Задает имя пути сервера для использования при открытии клиентского соединения. (Удаленные данные только для службы.)|  
  
 Остальные аргументы передаются для имени поставщика в *поставщика* аргумент без обработки с ADO.  
  
 Приложения HelloData в [HelloData: Простое приложение ADO](../../../ado/guide/data/hellodata-a-simple-ado-application.md) используется следующая строка подключения:  
  
```vb
m_sConnStr = "Provider=SQLOLEDB;Data Source=MySqlServer;" & _  
             "Initial Catalog=Northwind;Integrated Security='SSPI';"  
```  
  
 В этой строке подключения ADO распознает только `"Provider=SQLOLEDB"` параметр, который указывает поставщик Microsoft OLE DB для SQL Server в качестве источника данных ADO. Остальная часть пары аргумент/значение, `"Data Source=MySqlServer; Initial Catalog=Northwind;Integrated Security='SSPI';"`, передаются точные этого поставщика. Тип и допустимость такие параметры зависят от поставщика. Сведения о допустимых параметрах, которые могут быть переданы в строке подключения отдельный поставщик документации.  
  
 В соответствии с поставщик OLE DB для документации по SQL Server, можно заменить «Server» для *источника данных* параметр и «Database» для *Initial Catalog* параметра. Таким образом следующая строка подключения даст результаты, идентичные от приведенного выше:  
  
```vb
m_sConnStr = "Provider=SQLOLEDB;Server=MySqlServer;" & _  
             "Database=Northwind;Integrated Security='SSPI';"  
```
