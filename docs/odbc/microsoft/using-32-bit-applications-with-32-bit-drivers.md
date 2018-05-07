---
title: С помощью 32-разрядных приложений с 32-разрядными драйверами | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], 32-bit applications
- 32-bit applications with 32-bit drivers [ODBC]
ms.assetid: 0cdd5788-5642-4280-8d53-b4ec461aafa1
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7a07dae46125ce9ea04bfc36156d8855192396f3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-32-bit-applications-with-32-bit-drivers"></a>С помощью 32-разрядных приложений с 32-разрядными драйверами
Можно запустить 32-разрядных приложений с 32-разрядными драйверами. 32-разрядные приложения и 32-разрядные драйверы используют API-интерфейса Win32®.  
  
## <a name="architecture"></a>Architecture  
 На следующем рисунке показано, как 32-разрядным приложениям взаимодействовать с 32-разрядными драйверами. Приложение вызывает 32-разрядного диспетчера драйверов, который в свою очередь вызывает 32-разрядные драйверы.  
  
 ![Как 32&#45;взаимодействия разрядных приложений с 32&#45;разрядные драйверы](../../odbc/microsoft/media/sdka6.gif "sdka6")  
  
> [!IMPORTANT]  
>  Не используйте преобразования 32-разрядный установщик DLL на WindowsNT или Windows 2000. Несмотря на то, что он имеет то же имя файла как 32-разрядный установщик библиотеки DLL, это разные библиотеки DLL.  
  
## <a name="administration"></a>Администрирование  
 Источники данных для 32-разрядные драйверы можно управлять с помощью администратора источников данных ODBC. Чтобы открыть администратор ODBC на компьютерах под управлением Windows 2000, откройте панель управления Windows, дважды щелкните **Администрирование**, а затем дважды щелкните **источники данных (ODBC)**. На компьютерах под управлением предыдущих версий Microsoft Windows, значок называется **32-разрядная версия ODBC** или просто **ODBC**.  
  
## <a name="components"></a>Components  
 Компонент ODBC включает следующие файлы для запуска 32-разрядных приложений с 32-разрядными драйверами. Эти компоненты находятся в каталоге \Redist.  
  
|Имя файла|Описание|  
|---------------|-----------------|  
|Odbc32.dll|32-разрядный диспетчер драйверов|  
|Odbccp32.dll|32-разрядный установщик DLL|  
|Odbcad32.exe|32-разрядная программа Администратор ODBC|  
|Odbcinst.hlp|Файл справки программы установки|  
|Msvcrt40.dll|Библиотеки времени выполнения C|
