---
title: Устранение неполадок (драйвер ODBC для Visual FoxPro) | Документы Microsoft
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
- set ANSI [ODBC]
- troubleshooting Visual FoxPro ODBC driver [ODBC]
- remote views [ODBC]
- multitiered views [ODBC]
- parameterized views [ODBC], Visual FoxPro ODBC driver
- fetches [ODBC], Visual FoxPro ODBC driver
- positioned updates [ODBC]
- background fetching [ODBC]
ms.assetid: fd478dd8-666a-4f0a-a2d6-b94e81cbbe4b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23bab07c1f00abc9fb0d2c353603a21b58975933
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="troubleshooting-visual-foxpro-odbc-driver"></a>Устранение неполадок (драйвер ODBC для Visual FoxPro)
В следующих разделах рассматриваются способы повышения производительности и устранения проблем, которые могут возникнуть при использовании драйвера ODBC для Visual FoxPro.  
  
## <a name="accessing-parameterized-views"></a>Доступ к параметризованных представлений  
 Не удается получить доступ к параметризованных представлений в базе данных Visual FoxPro, с помощью драйвера. Параметризованные представления создает предложение WHERE в представлении SQL **ВЫБЕРИТЕ** инструкцию, которая ограничивает записи загружаются те записи, которые удовлетворяют условиям предложения WHERE, созданное с помощью указанное значение для параметра. Драйвер поддерживает передача параметров в представление, попытки получения доступа к параметризованные представления с помощью драйвера завершится ошибкой.  
  
 Значение параметра может быть указан во время выполнения или программно передана в представление.  
  
## <a name="accessing-remote-views"></a>Доступ к представлениям удаленного  
 Нет доступа к удаленной представлений в базе данных Visual FoxPro, с помощью драйвера. Удаленный представления являются, обращаться к данным не FoxPro или сочетание FoxPro и данные не FoxPro. Для доступа к удаленной представления, используйте Visual FoxPro.  
  
## <a name="deleting-records"></a>Удаление записей  
 Можно пометить записей для удаления с помощью драйвера, но не может окончательно удалить записи из базы данных. Чтобы окончательно удалить записи из таблицы, используйте Visual FoxPro.  
  
## <a name="increasing-performance-using-background-fetching"></a>Увеличение производительности с помощью выборки фона  
 С помощью фона выборка функции драйвера могут увеличить производительность в больших выборок. Выборка фона использует отдельный поток для выборки данных, запрошенных из определенного источника данных.  
  
 Можно использовать фон выборки для источника данных в одном из следующих способов:  
  
-   Проверьте **выборку данных в фоновом режиме** флажок на [диалоговое окно установки Visual FoxPro ODBC](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md).  
  
-   Используйте ключевое слово BackgroundFetch атрибут в строке подключения.  
  
 Сведения о ключевых словах атрибут строки подключения см. в разделе [с помощью строки подключения](../../odbc/microsoft/using-connection-strings.md).  
  
## <a name="updating-multitiered-views"></a>Обновление представлений многоуровневых  
 Представление многоуровневых — в представлении, основанном на одно или несколько представлений, а не для базовой таблицы. При обновлении данных в представлении многоуровневых обновления вышли из строя только один уровень в представление, на котором основывается представление верхнего уровня; базовые таблицы, не обновляются.  
  
## <a name="using-data-definition-language-ddl-in-stored-procedures"></a>С помощью языка описания данных (DDL) в хранимых процедурах  
 DDL, например CREATE TABLE или ALTER TABLE нельзя использовать в Visual FoxPro хранимых процедур.  
  
 Сведения о языке, можно использовать в хранимых процедурах см. в разделе [поддержка правила, триггеры, значения по умолчанию и хранимые процедуры](../../odbc/microsoft/support-rules-triggers-defaults-stored-procedures-visual-foxpro-odbc-driver.md).  
  
## <a name="using-positioned-updates"></a>С помощью позиционированные обновления  
 Драйвер не поддерживает позиционированные обновления. Используйте предложение SQL WHERE для определения строк, которые требуется обновить.  
  
## <a name="using-the-set-ansi-command"></a>При использовании команды SET ANSI  
 Если вы разработчик Visual FoxPro, должны учитывать, что SET ANSI по умолчанию является ON для драйвера, в отличие от значение по умолчанию для Visual FoxPro. Значение по умолчанию для параметра SET ANSI позволяет Visual FoxPro источников данных для согласованной работы с другими источниками данных ODBC, которые обычно выполняют точного сравнения. Можно изменить параметр по умолчанию. Дополнительные сведения см. в разделе [SET ANSI](../../odbc/microsoft/set-ansi-command.md).
