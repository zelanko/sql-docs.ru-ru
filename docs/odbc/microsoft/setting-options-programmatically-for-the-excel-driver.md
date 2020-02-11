---
title: Программная установка параметров для драйвера Excel | Документация Майкрософт
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
ms.openlocfilehash: 47181fca07aff7b2a0d418b8852cfce47cf9e501
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68063524"
---
# <a name="setting-options-programmatically-for-the-excel-driver"></a>Программная настройка параметров драйвера для Excel

|Параметр|Description|Метод|  
|------------|-----------------|------------|  
|Имя источника данных|Имя, идентифицирующее источник данных, например зарплату или персонал.|Чтобы динамически установить этот параметр, используйте ключевое слово **DSN** в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|База данных|Источник данных Microsoft Access можно настроить без выбора или создания базы данных. Если при установке не будет предоставлена база данных, пользователю будет предложено выбрать файл базы данных при подключении к источнику данных.|Чтобы динамически установить этот параметр, используйте ключевое слово **ДБК** в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Description|Необязательное описание данных в источнике данных; Например, "Дата найма, история заработной платы и текущий пересмотр всех сотрудников".|Чтобы динамически установить этот параметр, используйте ключевое слово **Description** в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Directory|Отображает текущий выбранный каталог.<br /><br /> Для файлов Microsoft Excel 3.0/4.0 путь отображается с меткой "каталог", а для файлов Microsoft Excel 5,0, 7,0 или 97, отображаемый путь помечен как "книга".|Чтобы динамически установить этот параметр, используйте ключевое слово **дефаултдир** в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Только чтение|Определяет базу данных как доступную только для чтения.|Чтобы динамически установить этот параметр, используйте ключевое слово **ReadOnly** в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Строки для проверки|Число строк для просмотра, по которым определяется тип данных каждого столбца. Тип данных определяется с учетом максимального числа найденных типов данных. Если обнаружены данные, не соответствующие типу данных, предполагаемому для столбца, то тип данных будет возвращен как значение NULL.<br /><br /> Для Microsoft Excel Driver можно ввести число от 1 до 16 строк для просмотра. Значение по умолчанию — 8; Если задано значение 0, просматриваются все строки. (Число за пределами ограничения будет возвращать ошибку.)|Чтобы динамически установить этот параметр, используйте ключевое слово **макссканровс** в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Выбор каталога|Отображает диалоговое окно, в котором можно выбрать каталог, содержащий файлы, к которым требуется получить доступ.<br /><br /> При определении каталога источника данных (для всех драйверов, кроме Microsoft Access) укажите каталог, в котором находятся наиболее часто используемые файлы. Драйвер ODBC использует этот каталог в качестве каталога по умолчанию. Если они часто используются, скопируйте другие файлы в этот каталог. Кроме того, можно уточнить имена файлов в инструкции SELECT с помощью имени каталога:<br /><br /> Выберите \* из к:\мидир\емп<br /><br /> Можно также указать новый каталог по умолчанию с помощью функции **SQLSetConnectOption** с параметром SQL_CURRENT_QUALIFIER.<br /><br /> Для файлов Microsoft Excel 3,0 или 4,0 путь отображается с меткой "каталог", а кнопка выбора пути помечена как "Select Directory" (Выбор каталога). Для файлов Microsoft Excel 5,0, 7,0 или 97 путь отображается с меткой "книга", а кнопка выбора пути помечена как "Выбор книги". При определении каталога источника данных укажите каталог, в котором находятся наиболее часто используемые файлы Microsoft Excel для Microsoft Excel 3.0/4.0, или каталог, в котором находится файл книги для Microsoft Excel 5,0, 7,0 или 97. Параметр **использовать текущий каталог** отключен для microsoft Excel 5,0, 7,0 и 97.|Чтобы динамически установить этот параметр, используйте ключевое слово **дефаултдир** в вызове [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|
