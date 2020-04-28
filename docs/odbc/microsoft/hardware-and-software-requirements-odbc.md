---
title: Требования к оборудованию и программному обеспечению (ODBC) | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe69775e379e9a9d661b4ddf81e577b738fcf34d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81295244"
---
# <a name="hardware-and-software-requirements-odbc"></a>Требования к оборудованию и программному обеспечению (ODBC)
В этом разделе перечислены требования к использованию драйверов для базы данных ODBC для настольных систем.  
  
## <a name="hardware-requirements"></a>Требования к оборудованию  
 Чтобы использовать драйверы базы данных ODBC для настольных систем, необходимо следующее:  
  
-   Персональный компьютер, совместимый с IBM.  
  
-   Жесткий диск с 6 МБ свободного дискового пространства.  
  
-   Не менее 16 МБ памяти произвольного доступа (ОЗУ).  
  
## <a name="software-requirements"></a>Требования к программному обеспечению  
 Для доступа к данным с помощью драйвера ODBC необходимо следующее:  
  
-   Драйвер ODBC.  
  
-   32-разрядный диспетчер драйверов ODBC версии 3,51 или более поздней (библиотеками odbc32. dll).  
  
-   Microsoft Windows 95 или более поздней версии или Windows NT 4,0 или Windows 2000.  
  
-   Размер стека не менее 20 КБ для приложения, использующего драйвер Microsoft ODBC.  
  
 При использовании Microsoft Windows NT 4,0 или Windows 2000 драйвер 32-bit является потокобезопасным, но только с помощью глобального семафора, управляющего доступом к драйверу. Параллельное использование драйвера в Windows NT ограничено. Для всех приложений, использующих ядро Microsoft Jet, весь доступ к слою ISAM.  
  
 При запуске нескольких 16-разрядных приложений в Windows в Windows (WOW) в Microsoft Windows NT 4,0 эти приложения должны быть запущены в отдельных дисковых пространствах. (Нельзя использовать то же пространство памяти, так как ODBC не поддерживает несколько сред в одном процессе.) Чтобы запустить приложение в отдельной области памяти, выберите значок приложения в диспетчере программ, откройте меню **файл** и выберите пункт **свойства**, а затем пункт **выполнить в отдельной области памяти**.  
  
 Использование этих драйверов 16-разрядными приложениями в Windows 95 не поддерживается.  
  
## <a name="driver-specific-hardware-and-software-requirements"></a>Требования к оборудованию и программному обеспечению для конкретного драйвера  
  
-   Микрософтакцесс и Дбаседриверс могут потребовать изменений в файлах Autoexec. bat или config. sys.
