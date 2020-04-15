---
title: Поддержка потока (Визуальный драйвер FoxPro ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- thread support [ODBC]
- Visual FoxPro ODBC driver [ODBC], thread support
- FoxPro ODBC driver [ODBC], thread support
- multithreaded applications [ODBC]
ms.assetid: 0c6abbbc-012b-41aa-bded-5e7e362d015b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2aa19eb233525b5a65ef67fe9903814fc1163177
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303085"
---
# <a name="thread-support-visual-foxpro-odbc-driver"></a>Поддержка потоков (драйвер ODBC для Visual FoxPro)
Визуальный Драйвер FoxPro ODBC является безопасным для потоков. Доступ к обработкам среды *(курица),* ручки соединения *(hdbc),* и ручки оператора *(hstmt*) обернут в соответствующие семафоры для предотвращения доступа к другим процессам и потенциального изменения внутренних структур данных водителя.  
  
 В многопоточном приложении можно отменить функцию, которая работает синхронно на *hstmt,* позвонив в [s'LCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md) на отдельном потоке.  
  
 Драйвер использует отдельный поток для получения данных при использовании прогрессивной извлечения. Чтобы использовать прогрессивный извлечения для источника данных, выберите **данные Fetch в фоновом** окне на [диалоговом окне ODBC Visual FoxPro Setup](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md) или используйте ключевое слово атрибута BackgroundFetch в строке соединения. Избегайте использования фонового привлечения при вызове драйвера из многопоточных приложений. Для получения информации о [ключевых словах](../../odbc/microsoft/using-connection-strings.md)атрибута строки соединения см.  
  
 Для получения более подробной информации о потоках *ODBC Programmer's Reference*и **S'LCancel** [см.](../../odbc/reference/syntax/sqlcancel-function.md)
