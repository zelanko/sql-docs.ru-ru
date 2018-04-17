---
title: Подключение с использованием файловых источников данных | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connecting to driver [ODBC], file data sources
- SQLDriverConnect function [ODBC], connecting using file data sources
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], file data sources
- file data sources [ODBC]
ms.assetid: 3003f8c2-8be6-41cc-8d9c-612e9bd0f3ae
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 70b0f5dd8c8ff133d1eb1b1a35c5ce24a7cc7ad5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="connecting-using-file-data-sources"></a>Подключение с использованием файловых источников данных
Сведения о соединении для источника данных хранятся в файле DSN с. В результате строки подключения можно использовать несколько раз одним пользователем или совместно несколькими пользователями, у них установлены соответствующие драйверы. Файл содержит имя драйвера (или другое имя источника данных в случае такие источники данных) и при необходимости строка подключения, который может использоваться с **SQLDriverConnect**. Диспетчер драйверов формирует строку подключения для вызова **SQLDriverConnect** из ключевых слов в файле DSN с.  
  
 Файл источника данных позволяет приложению указать параметры подключения, без необходимости построения строки подключения для использования с **SQLDriverConnect**. Источнику данных обычно создается путем указания **SAVEFILE** ключевое слово, которое вызывает диспетчера драйверов, чтобы сохранить строку подключения выходных данных, созданную с помощью вызова **SQLDriverConnect** файл DSN с. Можно повторно использовать строку подключения, вызвав **SQLDriverConnect** с **FILEDSN** ключевое слово. Это упрощает процесс подключения и постоянного источника строки подключения.  
  
 Файловые источники данных также можно создать путем вызова **SQLCreateDataSource** в программе установки библиотеки DLL. Сведения могут записываться в файл DSN с вызовом **SQLWriteFileDSN**и считываются из файла DSN с вызовом **SQLReadFileDSN**; обе эти функции также находятся в установщик DLL. Сведения об установщике DLL см. в разделе [Настройка источников данных](../../../odbc/reference/install/configuring-data-sources.md).  
  
 Ключевые слова, используемые для сведений о соединении, находятся в разделе [ODBC] DSN с файла. Минимальную информацию, будет иметь DSN с совместного использования файла в разделе [ODBC] является ключевое слово DRIVER:  
  
```  
DRIVER = SQL Server  
```  
  
 DSN совместного использования с файл обычно содержит строку подключения следующим образом:  
  
```  
DRIVER = SQL Server  
UID = Larry  
DATABASE = MyDB  
```  
  
 При непригоден для совместного использования файла источника данных DSN с файл содержит только **DSN** ключевое слово. Когда диспетчер драйверов отправляются сведения в такие источники данных, он подключается при необходимости для выбранного источника данных по **DSN** ключевое слово. Файл с расширением DSN непригоден для совместного использования с будет содержать следующее ключевое слово:  
  
```  
DSN = MyDataSource  
```  
  
 Строка подключения, используемая для источника данных представляет собой объединение ключевые слова, указанные в файле DSN с и ключевые слова, указанные в строке подключения в вызове **SQLDriverConnect**. Если ключевые слова в файле DSN с конфликтуют с помощью ключевых слов в строке подключения, диспетчер драйверов решает, следует использовать нужное значение ключевого слова. Дополнительные сведения см. в разделе [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="see-also"></a>См. также  
 [http://support.microsoft.com/kb/165866](http://support.microsoft.com/kb/165866)
