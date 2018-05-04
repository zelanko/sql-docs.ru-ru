---
title: Установка параметров программными средствами для драйвера Paradox | Документы Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Paradox driver
- Paradox driver [ODBC], setting options programmatically
- desktop database drivers [ODBC], Paradox driver
- Jet-based ODBC drivers [ODBC], Paradox driver
ms.assetid: 7996d3f8-b5f5-4cac-8a66-fc96a42b603e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f97de4ea57604b3f36984feea8ef942497017d4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="setting-options-programmatically-for-the-paradox-driver"></a>Настройка параметров программным образом с целью драйвера Paradox
|Параметр|Описание|Метод|  
|------------|-----------------|------------|  
|Каталог|Задает целевой каталог.|Чтобы задать этот параметр динамически, используйте **его значения** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Порядок сортировки|Последовательность, в которой отсортированы поля.<br /><br /> Последовательность может быть ASCII (по умолчанию), международного, Шведский финский или датский норвежский.|Чтобы задать этот параметр динамически, используйте **COLLATINGSEQUENCE** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Описание|Необязательное описание данных в источнике данных; Например «привлекает даты, журнал зарплат и текущий Обзор всех сотрудников.»|Чтобы задать этот параметр динамически, используйте **описание** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Монопольно|Если **монопольного** установлен, базы данных будут открыты в монопольном режиме и может осуществляться одновременно только одним пользователем. Повышение производительности достигается при работе в режиме монопольного доступа.|Чтобы задать этот параметр динамически, используйте **МОНОПОЛЬНОГО** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Тип сети|Стиль доступа к сети, используемый при доступе к данным Paradox: либо «3.*x*» для Paradox 3. *x* или «4. *x*» для Paradox 4. *x* или 5. *x*. Можно присвоить значение «3. *x*» или «4. *x*"Если версия Paradox 4. *x* или 5. *x*; Если версия Paradox 3. *x*, необходимо выбрать «3. *x*».|Чтобы задать этот параметр динамически, используйте **PARADOXNETSTYLE** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Время ожидания страницы|Указывает период времени, в десятых долях секунды страницы (если не используется), остаются в буфере до удаления. Значение по умолчанию — 600 десятые доли секунды (60 секунд). Этот параметр применяется ко всем источникам данных, использующие драйвер ODBC.<br /><br /> Время ожидания страницы не может быть 0, из-за задержки, обусловленные. Время ожидания страницы не может быть меньше специфические задержку, даже если параметр времени ожидания страницы имеет значение ниже этого значения.|Чтобы задать этот параметр динамически, используйте **PAGETIMEOUT** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Только для чтения|Определяет базу данных только для чтения.|Чтобы задать этот параметр динамически, используйте **READONLY** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Выберите каталог|Отображает диалоговое окно, где можно выбрать каталог, содержащий файлы, которым требуется доступ.<br /><br /> При определении каталога источника данных укажите каталог, где наиболее часто используемых файлов находятся. Драйвер ODBC использует этот каталог в качестве каталога по умолчанию. Скопируйте в эту папку, другие файлы, если часто используются. Кроме того можно указывать имена файлов в инструкции SELECT с именем каталога:<br /><br /> ВЫБЕРИТЕ \* ИЗ C:\MYDIR\EMP<br /><br /> Или можно указать новый каталог по умолчанию с помощью **SQLSetConnectOption** функцию с параметром SQL_CURRENT_QUALIFIER.|Чтобы задать этот параметр динамически, используйте **его значения** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Выбор сетевого каталога|Полный путь к каталогу, содержащему Paradox блокировки базы данных, так как она содержит файл Pdoxusrs.net (в Paradox 4. *x*) или в файле Paradox.net (на Paradox 5. *x*). Если каталог не содержит ни одного из этих файлов, создается драйвером Paradox. Дополнительные сведения об этих файлах см. в документации Paradox.<br /><br /> Перед выбором сетевого каталога, необходимо ввести имя пользователя Paradox в **имя пользователя** текстовое поле. Нажмите кнопку **Выбор сетевого каталога** для выбора сетевого каталога.|Чтобы задать этот параметр динамически, используйте **PARADOXNETPATH** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Имя пользователя|Имя пользователя Paradox. Это имя отображается для других пользователей файлов Paradox, когда встречается блокировка.|Чтобы задать этот параметр динамически, используйте **PARADOXUSERNAME** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|
