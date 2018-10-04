---
title: Оборудованию и программному обеспечению (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- hardware requirements [ODBC], desktop database drivers
- software requirements [ODBC], desktop database drivers
- system requirements [ODBC], desktop database drivers
- requirements [ODBC], desktop database drivers
ms.assetid: 6df2e9cd-de10-4629-97bd-32f2782616c7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b3f40621645aad2d1e52cb0a89baa8ff29b01446
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680662"
---
# <a name="hardware-and-software-requirements-odbc"></a>Требования к оборудованию и программному обеспечению (ODBC)
В этом разделе перечислены требования к использованию драйверов ODBC базы данных.  
  
## <a name="hardware-requirements"></a>Требования к оборудованию  
 Чтобы использовать драйверы для баз данных ODBC рабочего стола, необходимо иметь:  
  
-   IBM-совместимых персональный компьютер.  
  
-   Жесткий диск с 6 МБ свободного места на диске.  
  
-   Меньше 16 МБ памяти (ОЗУ).  
  
## <a name="software-requirements"></a>Требования к программному обеспечению  
 Для доступа к данным с помощью драйвера ODBC, необходимо иметь:  
  
-   Драйвер ODBC.  
  
-   32-разрядный диспетчер драйверов ODBC, версии 3.51 или более поздней версии (Odbc32.dll).  
  
-   Microsoft Windows 95 или более поздней версии, или Windows NT 4.0 или Windows 2000.  
  
-   Размер стека по крайней мере 20 КБ для приложения с помощью драйвера Microsoft ODBC.  
  
 При использовании Microsoft Windows NT 4.0 или Windows 2000, 32-разрядный драйвер является поточно ориентированной, но только при помощи глобального семафор, который управляет доступом к драйверу. Совместное использование драйвера ограничены в Windows NT. Весь доступ к уровню Jet ISAM будет один поток для всех приложений, использующих Microsoft Jet Database engine.  
  
 При использовании нескольких 16-разрядных приложений Windows on Windows (WOW) в Microsoft Windows NT 4.0, приложения должны выполняться в отдельном пространстве памяти. (Не использоваться то же пространство памяти, поскольку ODBC не поддерживает несколько сред в одном процессе.) Чтобы запустить приложение в отдельной области памяти, выберите значок приложения в руководитель программы, открыть **файл** меню и выберите пункт **свойства**и нажмите кнопку **запуска в отдельном памяти Пространство**.  
  
 Эти драйверы с 16-разрядных приложений в Windows 95 не поддерживается.  
  
## <a name="driver-specific-hardware-and-software-requirements"></a>Специфические для драйвера оборудованию и программному обеспечению  
  
-   MicrosoftAccess и dBASEdrivers могут потребоваться изменения в файлах Autoexec.bat и Config.sys.
