---
title: "Настройка параметров программным образом с целью драйвер Excel | Документы Microsoft"
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
- Jet-based ODBC drivers [ODBC], Excel driver
- desktop database drivers [ODBC], Excel driver
- ODBC desktop database drivers [ODBC], Excel driver
- Excel driver [ODBC], setting options programmatically
ms.assetid: b5ee3636-4591-427a-a65a-a2d5926fcc1a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: da1f2ed6bbca3709c8223713f4841ed34288f5a3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setting-options-programmatically-for-the-excel-driver"></a>Настройка параметров программным образом с целью драйвер Excel
|Параметр|Description|Метод|  
|------------|-----------------|------------|  
|Имя источника данных|Имя, идентифицирующее источник данных, например Payroll или службу.|Чтобы задать этот параметр динамически, используйте **DSN** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|База данных|Можно настроить источник данных Microsoft Access, без выбора или создания базы данных. Если база данных не предоставляется при установке, пользователю будет предложено выбрать файл базы данных при подключении к источнику данных.|Чтобы задать этот параметр динамически, используйте **DBQ** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Description|Необязательное описание данных в источнике данных; Например «привлекает даты, журнал зарплат и текущий Обзор всех сотрудников.»|Чтобы задать этот параметр динамически, используйте **описание** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Каталог|Отображает текущий выбранный каталог.<br /><br /> Для файлов Microsoft Excel 3.0 или 4.0 отображения пути меткой «Directory», то время как для Microsoft Excel 5.0 7.0 или 97 файлы, отображение пути меткой «Книга».|Чтобы задать этот параметр динамически, используйте **его значения** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Только для чтения|Определяет базу данных только для чтения.|Чтобы задать этот параметр динамически, используйте **READONLY** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Строк для просмотра|Число строк для сканирования, чтобы определить тип данных каждого столбца. Тип данных определяется заданным максимальное количество типов данных. Если данные, не соответствует типу данных, указанному для столбца, тип данных будет возвращаться как значение NULL.<br /><br /> Для драйвера Microsoft Excel можно ввести число от 1 до 16 для строк для сканирования. По умолчанию используется значение 8. Если свойство имеет значение 0, просматриваются все строки. (Число за пределами ограничение будет возвращена ошибка.)|Чтобы задать этот параметр динамически, используйте **MAXSCANROWS** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Выберите каталог|Отображает диалоговое окно, где можно выбрать каталог, содержащий файлы, которым требуется доступ.<br /><br /> При определении каталога источника данных (для всех драйверов, за исключением Microsoft Access), укажите каталог, где находятся наиболее часто используемых файлов. Драйвер ODBC использует этот каталог в качестве каталога по умолчанию. Скопируйте в эту папку, другие файлы, если часто используются. Кроме того можно указывать имена файлов в инструкции SELECT с именем каталога:<br /><br /> ВЫБЕРИТЕ \* ИЗ C:\MYDIR\EMP<br /><br /> Или можно указать новый каталог по умолчанию с помощью **SQLSetConnectOption** функцию с параметром SQL_CURRENT_QUALIFIER.<br /><br /> Для Microsoft Excel 3.0 или 4.0 файлы отображение пути меткой «Directory» и выбора «путь» называется «Выбор каталога». Для файлов Microsoft Excel 5.0, 7.0 или 97 отображения пути меткой «Книга» и кнопку выбора пути меткой «Выбор книги». При определении каталога источника данных, укажите каталог, где расположены для Microsoft Excel 3.0 или 4.0 наиболее часто используемые файлы Microsoft Excel, или каталог, где находится файл книги для Microsoft Excel 5.0, 7.0 или 97. **Использовать текущий каталог** отключена для Microsoft Excel 5.0, 7.0 и 97.|Чтобы задать этот параметр динамически, используйте **его значения** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|

