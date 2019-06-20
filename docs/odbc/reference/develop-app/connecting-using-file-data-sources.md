---
title: Подключение с использованием файловых источников данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to driver [ODBC], file data sources
- SQLDriverConnect function [ODBC], connecting using file data sources
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], file data sources
- file data sources [ODBC]
ms.assetid: 3003f8c2-8be6-41cc-8d9c-612e9bd0f3ae
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6fec2cea71ba818e955e0b6c2ce31c58f2c07357
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63043889"
---
# <a name="connecting-using-file-data-sources"></a>Подключение с использованием файловых источников данных
Сведения о соединении для источника данных хранится в файле .dsn. Таким образом строку подключения можно использовать несколько раз одним пользователем или совместно использовать несколько пользователей, если они имеют установлены соответствующие драйверы. Файл содержит имя драйвера (или другой источник данных в случае такие источники данных) и при необходимости строка подключения, который может использоваться с **SQLDriverConnect**. Диспетчер драйверов формирует строку подключения для вызова **SQLDriverConnect** из ключевых слов в файле .dsn.  
  
 Файл источника данных позволяет приложению указать параметры подключения без необходимости создавать строку подключения для использования с **SQLDriverConnect**. Источнику данных обычно создается путем указания **SAVEFILE** ключевое слово, которое вызывает диспетчера драйверов для сохранения полученную строку подключения, созданные с помощью вызова **SQLDriverConnect** .dsn файл. Можно многократно использовать строку подключения, вызвав **SQLDriverConnect** с **FILEDSN** ключевое слово. Это упрощает процесс подключения и предоставляет постоянный источник строки подключения.  
  
 Файловые источники данных также могут создаваться путем вызова **SQLCreateDataSource** в установщике библиотеки DLL. Данные могут быть записаны в файл .dsn путем вызова **SQLWriteFileDSN**и чтения из файла .dsn путем вызова **SQLReadFileDSN**; обе эти функции также ведется библиотека DLL установщика. Сведения об установщике библиотеки DLL, см. в разделе [Настройка источников данных](../../../odbc/reference/install/configuring-data-sources.md).  
  
 Ключевые слова, используемые для подключения сведения приведены в разделе [ODBC] файла .dsn. Минимум информации, которое файл .dsn совместного использования окажет в разделе [ODBC] — это ключевое слово DRIVER:  
  
```  
DRIVER = SQL Server  
```  
  
 Файл совместного использования .dsn обычно содержит строку подключения следующим образом:  
  
```  
DRIVER = SQL Server  
UID = Larry  
DATABASE = MyDB  
```  
  
 Когда такие источнику данных, файл .dsn содержит только **DSN** ключевое слово. Когда диспетчер драйверов отправляются сведения в такие источники данных, он подключается при необходимости для источника данных, указанного по **DSN** ключевое слово. В такие .dsn файл должен содержать следующее ключевое слово:  
  
```  
DSN = MyDataSource  
```  
  
 Строка подключения, используемая для источника данных представляет собой объединение ключевые слова, указанные в файле .dsn и ключевые слова, указанные в строке подключения в вызове **SQLDriverConnect**. Если ключевые слова в файле .dsn конфликтуют с ключевыми словами в строке подключения, диспетчер драйверов решает, следует использовать значение ключевого слова. Дополнительные сведения см. в разделе [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="see-also"></a>См. также  
 [https://support.microsoft.com/kb/165866](https://support.microsoft.com/kb/165866)
