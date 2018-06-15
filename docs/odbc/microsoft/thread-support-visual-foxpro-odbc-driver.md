---
title: Поддержка (драйвер ODBC для Visual FoxPro) потоков | Документы Microsoft
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
- thread support [ODBC]
- Visual FoxPro ODBC driver [ODBC], thread support
- FoxPro ODBC driver [ODBC], thread support
- multithreaded applications [ODBC]
ms.assetid: 0c6abbbc-012b-41aa-bded-5e7e362d015b
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 75adc2f72071765dc705d34b2bdd577316ae1acf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32905649"
---
# <a name="thread-support-visual-foxpro-odbc-driver"></a>Поддержка потоков (драйвер ODBC для Visual FoxPro)
Драйвер ODBC для Visual FoxPro является потокобезопасным. Доступ к среде дескрипторов (*огда*), дескрипторов соединений (*hdbc*) и дескрипторы инструкций (*hstmt*) упаковывается в соответствующие семафоры для предотвращения других процессов доступ и потенциально изменяя драйвера внутренних структур данных.  
  
 В многопоточном приложении, можно отменить функции, на котором выполняется синхронно на *hstmt* путем вызова [SQLCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md) в отдельном потоке.  
  
 Драйвер использует отдельный поток для выборки данных при использовании последовательной выборки. Последовательная выборка для источника данных, установите **выборку данных в фоновом режиме** флажок на [диалоговое окно установки Visual FoxPro ODBC](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md) или используйте ключевое слово атрибут BackgroundFetch подключения Строка. Избегайте использования выборку в фоновом режиме, при вызове драйвер из многопоточных приложений. Сведения о ключевых словах атрибут строки соединения см. в разделе [с помощью строки подключения](../../odbc/microsoft/using-connection-strings.md).  
  
 Дополнительные сведения о потоках и **SQLCancel**, в разделе [SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md) в *справочнике программиста ODBC*.
