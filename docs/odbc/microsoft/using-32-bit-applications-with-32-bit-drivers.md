---
title: Использование 32-bit-приложений с 32-bit драйверами (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], 32-bit applications
- 32-bit applications with 32-bit drivers [ODBC]
ms.assetid: 0cdd5788-5642-4280-8d53-b4ec461aafa1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31512f9339b9d46225bb4f1198cb617a48509acb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307605"
---
# <a name="using-32-bit-applications-with-32-bit-drivers"></a>Использование 32-разрядных приложений с 32-разрядными драйверами
Вы можете запускать 32-разрядные приложения с 32-битными драйверами. 32-разрядные приложения и 32-битные драйверы используют API Win32®.  
  
## <a name="architecture"></a>Architecture  
 Следующая иллюстрация показывает, как 32-битные приложения взаимодействуют с 32-битными драйверами. Приложение вызывает 32-битный менеджер драйвера, который, в свою очередь, вызывает 32-битных драйверов.  
  
 ![Как 32&#45;битовых приложений общаются с 32&#45;драйверами бита](../../odbc/microsoft/media/sdka6.gif "sdka6")  
  
> [!IMPORTANT]  
>  Не используйте 32-битный тукинг установщик DLL на WindowsNT/Windows2000. Хотя он имеет то же имя файла, как 32-разрядный установщик DLL, это другой DLL.  
  
## <a name="administration"></a>Администрирование  
 Управлять источниками данных для 32-битных драйверов можно с помощью администратора ODBC Data Source. Чтобы открыть администраторODБ на компьютерах под управлением Windows 2000, откройте панель управления Windows, дважды щелкните **административные инструменты,** а затем дважды щелкните **источники данных (ODBC).** На компьютерах, работающих в предыдущих версиях Microsoft Windows, значок называется **32-битный ODBC** или просто **ODBC**.  
  
## <a name="components"></a>Components  
 Компонент ODBC включает в себя следующие файлы для запуска 32-битных приложений с 32-битными драйверами. Эти компоненты находятся в каталоге «Redist».  
  
|Имя файла|Описание|  
|---------------|-----------------|  
|Odbc32.dll|32-разрядный менеджер драйвера|  
|Odbccp32.dll|32-разрядный установщик DLL|  
|Odbcad32.exe|32-битная программа администратора ODBC|  
|Odbcinst.hlp|Файл справки установки|  
|Msvcrt40.dll|C библиотека времени выполнения|
