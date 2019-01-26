---
title: Программная настройка параметров для драйвера Excel | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], Excel driver
- desktop database drivers [ODBC], Excel driver
- ODBC desktop database drivers [ODBC], Excel driver
- Excel driver [ODBC], setting options programmatically
ms.assetid: b5ee3636-4591-427a-a65a-a2d5926fcc1a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 271f61247b6083abd31657fe319bce234bc16f50
ms.sourcegitcommit: 1e28f923cda9436a4395a405ebda5149202f8204
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55044341"
---
# <a name="setting-options-programmatically-for-the-excel-driver"></a>Программная настройка параметров драйвера для Excel

|Параметр|Описание|Метод|  
|------------|-----------------|------------|  
|Имя источника данных|Имя, определяющее источник данных, таких как расчет заработной платы или сотрудникам.|Чтобы задать этот параметр динамически, используйте **DSN** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|База данных|Без выбора или создания базы данных можно настроить источник данных Microsoft Access. Если база данных не предоставляется при установке, пользователю будет предложено выбрать файл базы данных при подключении к источнику данных.|Чтобы задать этот параметр динамически, используйте **DBQ** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Описание|Необязательное описание данных в источнике данных; Например «Hire даты, журнал зарплат и текущий Обзор всех сотрудников.»|Чтобы задать этот параметр динамически, используйте **описание** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Каталог|Отображает текущий выбранный каталог.<br /><br /> Для файлов Microsoft Excel 3.0 или 4.0, отображение пути имеет метку «Каталог», а для Microsoft Excel 5.0 7.0 или 97 файлы, отображение пути имеет метку «Книга».|Чтобы задать этот параметр динамически, используйте **его значения** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Только для чтения|Определяет базу данных только для чтения.|Чтобы задать этот параметр динамически, используйте **READONLY** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Строк для просмотра|Количество строк, чтобы просмотреть, чтобы определить тип данных каждого столбца. Тип данных определяется максимальное количество типов данных. Если в данных, не соответствует типу данных, указанному для столбца, тип данных будет возвращаться как значения NULL.<br /><br /> Для драйвера Microsoft Excel можно ввести число от 1 до 16 для строки для поиска. По умолчанию используется значение 8; Если он имеет значение 0, просматриваются все строки. (Лежащее за пределами ограничения возвратит ошибку.)|Чтобы задать этот параметр динамически, используйте **MAXSCANROWS** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Выберите каталог|Отображает диалоговое окно, в котором можно выбрать каталог, содержащий файлы, которые необходимо получить доступ.<br /><br /> При определении каталога источника данных (для всех драйверов, за исключением Microsoft Access), укажите каталог, где находятся наиболее часто используемых файлов. Драйвер ODBC использует этот каталог в качестве каталога по умолчанию. Скопируйте другие файлы в этот каталог, если они используются часто. Кроме того можно уточнить имена файлов в инструкции SELECT с именем каталога:<br /><br /> ВЫБЕРИТЕ \* ИЗ C:\MYDIR\EMP<br /><br /> Или можно указать новый каталог по умолчанию с помощью **SQLSetConnectOption** функцию с параметром SQL_CURRENT_QUALIFIER.<br /><br /> Для Microsoft Excel 3.0 или 4.0 файлы отображение пути имеет метку «Directory» и кнопка выбора пути называется «Выбор каталога». Для файлов Microsoft Excel 5.0, 7.0 или 97 Отображение пути имеет метку «Книги» и кнопка выбора пути называется «Выбор книги». При определении каталога источника данных, укажите каталог, где наиболее часто используемых файлов Microsoft Excel для Microsoft Excel 3.0 или 4.0, или каталог, где находится файл книги для Microsoft Excel 5.0, 7.0 или 97. **Использовать текущий каталог** отключена для Microsoft Excel 5.0, 7.0 и 97.|Чтобы задать этот параметр динамически, используйте **его значения** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|
