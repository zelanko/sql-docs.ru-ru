---
title: Требования к оборудованию и программному обеспечению (ODBC) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295244"
---
# <a name="hardware-and-software-requirements-odbc"></a>Требования к оборудованию и программному обеспечению (ODBC)
В этой теме перечислены требования к использованию драйверов настольных баз данных ODBC.  
  
## <a name="hardware-requirements"></a>Требования к оборудованию  
 Для использования драйверов базы данных на настольных компьютерах ODBC необходимо:  
  
-   Персональный компьютер, совместимый с IBM.  
  
-   Твердый диск с 6 МБ свободного дискового пространства.  
  
-   Не менее 16 МБ памяти случайного доступа (RAM).  
  
## <a name="software-requirements"></a>Требования к программному обеспечению  
 Чтобы получить доступ к данным с помощью драйвера ODBC, необходимо:  
  
-   Водитель ODBC.  
  
-   32-разрядный менеджер драйвера ODBC, версия 3.51 или более поздняя (Odbc32.dll).  
  
-   Microsoft Windows 95 или позже, или Windows NT 4.0 или Windows 2000.  
  
-   Размер стека не менее 20 кБ для приложения с помощью драйвера Microsoft ODBC.  
  
 При использовании Microsoft Windows NT 4.0 или Windows 2000 32-разрядный драйвер является безопасным для потоков, но только с помощью глобального семафора, который контролирует доступ к драйверу. Одновременное использование драйвера очень ограничено под Windows NT. Весь доступ к слою Jet ISAM будет однопониченным для всех приложений с помощью движка Microsoft Jet.  
  
 При запуске нескольких 16-разрядных приложений на Windows на Windows (WOW) на Microsoft Windows NT 4.0, приложения должны быть запущены в отдельных пространствах памяти. (Одно и то же пространство памяти не может быть использовано, потому что ODBC не поддерживает несколько сред в одном и том же процессе.) Чтобы запустить приложение в отдельном пространстве памяти, выберите значок приложения в менеджере программы, откройте меню **файла** и нажмите **Свойства,** а затем нажмите **Run In Separate Memory Space.**  
  
 Использование этих драйверов 16-битными приложениями на Windows 95 не поддерживается.  
  
## <a name="driver-specific-hardware-and-software-requirements"></a>Требования к оборудованию и программному обеспечению для драйверов  
  
-   MicrosoftAccess и dBASEdrivers могут потребовать изменений в файлах Autoexec.bat или Config.sys.
