---
title: Программная настройка параметров для драйвер для Paradox | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Paradox driver
- Paradox driver [ODBC], setting options programmatically
- desktop database drivers [ODBC], Paradox driver
- Jet-based ODBC drivers [ODBC], Paradox driver
ms.assetid: 7996d3f8-b5f5-4cac-8a66-fc96a42b603e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 50862270598172f8ff9e8572e9f201cbeb826bc5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47637242"
---
# <a name="setting-options-programmatically-for-the-paradox-driver"></a>Программная настройка параметров драйвера для Paradox
|Параметр|Описание|Метод|  
|------------|-----------------|------------|  
|Каталог|Задает целевой каталог.|Чтобы задать этот параметр динамически, используйте **его значения** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Порядок сортировки|Последовательность, в которой сортируется поля.<br /><br /> Последовательность может быть ASCII (по умолчанию), международный, Шведский финский или Norwegian-Danish.|Чтобы задать этот параметр динамически, используйте **COLLATINGSEQUENCE** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Описание|Необязательное описание данных в источнике данных; Например «Hire даты, журнал зарплат и текущий Обзор всех сотрудников.»|Чтобы задать этот параметр динамически, используйте **описание** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Монопольно|Если **эксклюзивные** установлен, базы данных будет открыт в монопольном режиме и может осуществляться только одним пользователем одновременно. Повышение производительности достигается при работе в монопольном режиме.|Чтобы задать этот параметр динамически, используйте **ЭКСКЛЮЗИВНЫЕ** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Тип сети|Стиль доступа к сети, используемый при доступе к данным Paradox: либо «3.*x*"для Paradox 3. *x* или «4. *x*"для Paradox 4. *x* или 5. *x*. Можно установить значение «3. *x*"или «4. *x*"Если версия Paradox 4. *x* или 5. *x*; Если версия Paradox 3. *x*, стиль должен быть «3. *x*«.|Чтобы задать этот параметр динамически, используйте **PARADOXNETSTYLE** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Время ожидания страницы|Указывает период времени, в десятых долях секунды страницы (если не используется), остаются в буфере до их удаления. Значение по умолчанию — 600 десятые доли секунды (60 секунд). Этот параметр применяется ко всем источникам данных, использующие драйвер ODBC.<br /><br /> Время ожидания страницы не может быть 0, из-за присущие задержки. Время ожидания страницы не может быть меньше присущие задержку, даже если параметр времени ожидания страницы имеет значение ниже этого значения.|Чтобы задать этот параметр динамически, используйте **PAGETIMEOUT** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Только для чтения|Определяет базу данных только для чтения.|Чтобы задать этот параметр динамически, используйте **READONLY** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Выберите каталог|Отображает диалоговое окно, в котором можно выбрать каталог, содержащий файлы, которые необходимо получить доступ.<br /><br /> При определении каталога источника данных укажите каталог, где наиболее часто используемых файлов расположены. Драйвер ODBC использует этот каталог в качестве каталога по умолчанию. Скопируйте другие файлы в этот каталог, если они используются часто. Кроме того можно уточнить имена файлов в инструкции SELECT с именем каталога:<br /><br /> ВЫБЕРИТЕ \* ИЗ C:\MYDIR\EMP<br /><br /> Или можно указать новый каталог по умолчанию с помощью **SQLSetConnectOption** функцию с параметром SQL_CURRENT_QUALIFIER.|Чтобы задать этот параметр динамически, используйте **его значения** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Выберите сетевой каталог|Полный путь к каталогу, содержащему Paradox блокировки базы данных, так как она содержит файл Pdoxusrs.net (в Paradox 4. *x*) или файл Paradox.net (на Paradox 5. *x*). Если каталог не содержит один из этих файлов, драйвер для Paradox создаст его. Сведения об этих файлах см. в документации для Paradox.<br /><br /> Перед выбором в сетевую папку, необходимо ввести имя пользователя для Paradox в **имя пользователя** текстовое поле. Нажмите кнопку **выберите сетевой каталог** для выбора в сетевую папку.|Чтобы задать этот параметр динамически, используйте **PARADOXNETPATH** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Имя пользователя|Имя пользователя для Paradox. Это имя отображается для других пользователей файлов Paradox, когда встречается блокировка.|Чтобы задать этот параметр динамически, используйте **PARADOXUSERNAME** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|
