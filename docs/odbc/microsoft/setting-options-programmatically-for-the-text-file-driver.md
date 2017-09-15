---
title: "Установка параметров программными средствами для драйвера текстового файла | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text file driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], text file driver
- desktop database drivers [ODBC], text file driver
- Jet-based ODBC drivers [ODBC], text file driver
ms.assetid: cbde2ca1-5d4e-4444-a371-a72f3ac4d92a
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d5037ca7d41470a2e9f7ce342ab49b08a6af0d74
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setting-options-programmatically-for-the-text-file-driver"></a>Установка параметров программными средствами для драйвера текстового файла
|Параметр|Description|Метод|  
|------------|-----------------|------------|  
|Имя источника данных|Имя, идентифицирующее источник данных, например Payroll или службу.|Чтобы задать этот параметр динамически, используйте **DSN** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Определение формата|Отображает **Определение текстового формата** диалоговое окно и позволяет указать схему для отдельных таблиц в каталоге источника данных.|Этот параметр не может быть задана динамически с помощью вызова [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Description|Необязательное описание данных в источнике данных; Например «привлекает даты, журнал зарплат и текущий Обзор всех сотрудников.»|Чтобы задать этот параметр динамически, используйте **описание** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Каталог|Выбор целевой каталог.|Чтобы задать этот параметр динамически, используйте **его значения** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Список расширений|Список расширений имен файлов текстовых файлов в источнике данных. При использовании драйвера текстового файла без расширения, создается при выполнении инструкции CREATE TABLE с именем, которое не имеет расширения. Других драйверов создайте файл с расширением по умолчанию, если расширение не указан. Создание файла с расширением txt, расширения должны быть включены в имя. Для отображения файлов без расширений в **Определение текстового формата** диалоговое окно «», «*.» необходимо добавить в список расширений.|Чтобы задать этот параметр динамически, используйте **расширения** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Только для чтения|Определяет базу данных только для чтения.|Чтобы задать этот параметр динамически, используйте **READONLY** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Строк для просмотра|Число строк для сканирования, чтобы определить тип данных каждого столбца. Тип данных определяется заданным максимальное количество типов данных. Если данные, не соответствует типу данных, указанному для столбца, тип данных будет возвращаться как значение NULL.<br /><br /> Для драйвера текста можно ввести число от 1 до 32767 для числа строк для сканирования; Тем не менее значение по умолчанию всегда 25. (Число за пределами ограничение будет возвращена ошибка.)|Чтобы задать этот параметр динамически, используйте **MAXSCANROWS** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Выберите каталог|Отображает диалоговое окно, где можно выбрать каталог, содержащий файлы, которым требуется доступ.<br /><br /> При определении каталога источника данных укажите каталог, где наиболее часто используемых файлов находятся. Драйвер ODBC использует этот каталог в качестве каталога по умолчанию. Скопируйте в эту папку, другие файлы, если часто используются. Кроме того можно указывать имена файлов в инструкции SELECT с именем каталога:`SELECT * FROM C:\MYDIR\EMP`<br /><br /> Или можно указать новый каталог по умолчанию с помощью **SQLSetConnectOption** функцию с параметром SQL_CURRENT_QUALIFIER.|Чтобы задать этот параметр динамически, используйте **его значения** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|
