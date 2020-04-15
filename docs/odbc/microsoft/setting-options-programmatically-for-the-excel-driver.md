---
title: Настройка параметры программно для драйвера Excel (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1fcd5542e4beee1f7c7a30d5e0ee9f2815a3f0b6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300774"
---
# <a name="setting-options-programmatically-for-the-excel-driver"></a>Программная настройка параметров драйвера для Excel

|Параметр|Описание|Метод|  
|------------|-----------------|------------|  
|Имя базы данных-источника|Имя, идентифицирует источник данных, например, платежная ведомость или персонал.|Чтобы установить эту опцию динамически, используйте ключевое слово **DSN** в вызове на [S'LConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|База данных|Источник данных Microsoft Access можно настроить без выбора или создания базы данных. Если при настройке не предусмотрена база данных, пользователю будет предложено выбрать файл базы данных при подключении к источнику данных.|Чтобы установить эту опцию динамически, используйте ключевое слово **DB'** в вызове на [S'LConfigDataSource.](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)|  
|Описание|Дополнительное описание данных в источнике данных; например, "Дата найма, история заработной платы и текущий обзор всех сотрудников".|Чтобы установить эту опцию динамически, используйте ключевое слово **ОПИСАНИЕ** в вызове на [S'LConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Каталог|Отображает выбранный в настоящее время каталог.<br /><br /> Для файлов Microsoft Excel 3.0/4.0 дисплей пути помечен как "Каталог", в то время как для файлов Microsoft Excel 5.0, 7.0 или 97— дисплей пути помечен как "Workbook".|Чтобы установить эту опцию динамически, используйте ключевое слово **DEFAULTDIR** в вызове на [S'LConfigDataSource.](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)|  
|Только для чтения|Обозначает базу данных только для чтения.|Чтобы установить эту опцию динамически, используйте ключевое слово **READONLY** в вызове на [S'LConfigDataSource.](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)|  
|Строки для сканирования|Количество строк для сканирования для определения типа данных каждого столбца. Тип данных определяется с учетом максимального количества найденных видов данных. При обнаружении данных, не совпадающих с типом данных, угадываемым для столбца, тип данных будет возвращен в качестве значения NULL.<br /><br /> Для драйвера Microsoft Excel можно ввести номер от 1 до 16 для сканирования строк. Значение по умолчанию до 8; если он установлен до 0, все строки сканируются. (Номер за пределами лимита вернет ошибку.)|Чтобы установить эту опцию динамически, используйте ключевое слово **MAXSCANROWS** в вызове на [S'LConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Выберите каталог|Отображает диалоговую будку, где можно выбрать каталог, содержащий файлы, к которые вы хотите получить доступ.<br /><br /> При определении каталога исходных данных (для всех драйверов, кроме Microsoft Access), укажите каталог, где находятся наиболее часто используемые файлы. Драйвер ODBC использует этот каталог в качестве каталога по умолчанию. Копирование других файлов в этот каталог, если они используются часто. Кроме того, вы можете квалифицировать имена файлов в выписке SELECT с именем каталога:<br /><br /> СЕЛЕКТ \* От С: »МИДИР-ЭМП<br /><br /> Кроме того, можно указать новый каталог по умолчанию, используя функцию **S'LSetConnectOption** с SQL_CURRENT_QUALIFIER опцией.<br /><br /> Для файлов Microsoft Excel 3.0 или 4.0 дисплей пути помечен как "Каталог", а кнопка выбора пути - "Выбрать каталог". Для файлов Microsoft Excel 5.0, 7.0 или 97— дисплей пути помечен как "Workbook", а кнопка выбора пути - "Выбрать рабочую книгу". При определении каталога исходных данных укажите каталог, в котором находятся наиболее часто используемые файлы Microsoft Excel для Microsoft Excel 3.0/4.0, или каталог, в котором находится файл рабочей книги для Microsoft Excel 5.0, 7.0 или 97. **Используйте текущий каталог** отключен для Microsoft Excel 5.0, 7.0 и 97.|Чтобы установить эту опцию динамически, используйте ключевое слово **DEFAULTDIR** в вызове на [S'LConfigDataSource.](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)|
