---
title: "Оборудованию и программному обеспечению (ODBC) | Документы Microsoft"
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
- hardware requirements [ODBC], desktop database drivers
- software requirements [ODBC], desktop database drivers
- system requirements [ODBC], desktop database drivers
- requirements [ODBC], desktop database drivers
ms.assetid: 6df2e9cd-de10-4629-97bd-32f2782616c7
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2545fba508ef3862834743ddaa8dd74183123b30
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="hardware-and-software-requirements-odbc"></a>Оборудованию и программному обеспечению (ODBC)
В этом разделе перечислены требования к использованию драйверы ODBC системной базы данных.  
  
## <a name="hardware-requirements"></a>Требования к оборудованию  
 Чтобы использовать драйверы ODBC системной базы данных, необходимо иметь:  
  
-   IBM-совместимых персональный компьютер.  
  
-   Жесткий диск с 6 МБ свободного места на диске.  
  
-   Меньше 16 МБ памяти (ОЗУ).  
  
## <a name="software-requirements"></a>Требования к программному обеспечению  
 Для доступа к данным с помощью драйвера ODBC, необходимо иметь:  
  
-   Драйвер ODBC.  
  
-   32-разрядные диспетчер драйверов ODBC, версии 3.51 или более поздней версии (Odbc32.dll).  
  
-   Microsoft Windows 95 или более поздней версии, Windows или Windows NT 4.0 или Windows 2000.  
  
-   Размер стека по крайней мере 20 КБ для приложения с помощью драйвера Microsoft ODBC.  
  
 При использовании Microsoft Windows NT 4.0 или Windows 2000, 32-разрядный драйвер является потокобезопасным, но только с помощью глобального семафора, которая управляет доступом к драйверу. Совместное использование драйвера ограничены в Windows NT. Все доступ слой Jet ISAM будет однопоточных для всех приложений, использующих ядра Microsoft Jet.  
  
 При запуске нескольких 16-разрядных приложений в Windows on Windows (WOW) в Microsoft Windows NT 4.0, приложения должны выполняться в отдельном пространстве памяти. (Нельзя использовать то же пространство памяти, поскольку ODBC не поддерживает несколько сред в том же процессе.) Чтобы запустить приложение в отдельной области памяти, выберите значок приложения в диспетчере программ откройте **файл** меню и выберите пункт **свойства**и нажмите кнопку **запустить отдельную память Место**.  
  
 Использовать эти драйверы с 16-разрядных приложений в Windows 95 не поддерживается.  
  
## <a name="driver-specific-hardware-and-software-requirements"></a>Специфические для драйвера оборудованию и программному обеспечению  
  
-   MicrosoftAccess и dBASEdrivers могут потребовать внесения изменений в файлы Autoexec.bat и Config.sys.
