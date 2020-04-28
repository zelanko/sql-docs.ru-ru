---
title: Поддержка потоков (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303085"
---
# <a name="thread-support-visual-foxpro-odbc-driver"></a>Поддержка потоков (драйвер ODBC для Visual FoxPro)
Драйвер ODBC для Visual FoxPro является потокобезопасным. Доступ к дескрипторам среды (пределам *),* дескрипторам подключений (*хдбк*) и дескрипторам инструкций (*хстмт*) заключается в подходящих семафорах, чтобы другие процессы не обращались к внутренним структурам данных драйвера и могут изменять их.  
  
 В многопоточном приложении можно отменить функцию, выполняющуюся синхронно, в *хстмт* , вызвав [SQLCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md) в отдельном потоке.  
  
 Драйвер использует отдельный поток для выборки данных при использовании прогрессивной выборки. Чтобы использовать прогрессивную выборку для источника данных, установите флажок **получить данные в фоновом режиме** в [диалоговом окне установки ODBC Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md) или используйте ключевое слово атрибута баккграундфетч в строке подключения. Избегайте использования фоновой выборки при вызове драйвера из многопоточных приложений. Дополнительные сведения о ключевых словах атрибутов строки подключения см. [в разделе Использование строк подключения](../../odbc/microsoft/using-connection-strings.md).  
  
 Дополнительные сведения о потоках и **SQLCancel**см. в разделе [SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md) в *справочнике программиста по ODBC*.
