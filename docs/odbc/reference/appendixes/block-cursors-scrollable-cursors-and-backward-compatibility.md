---
title: Блочные курсоры, Прокручиваемые курсоры и обратной совместимости | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], backward compatibility
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- block cursors [ODBC]
ms.assetid: d9d271f6-d2d9-49b9-a365-4909ca06caae
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7e25e546b359dd7178739e074664c3239fcfbdba
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility"></a>Блочные курсоры, Прокручиваемые курсоры и обратная совместимость
На наличие **SQLFetchScroll** и **SQLExtendedFetch** представляет первый clear разбиения в ODBC между приложения программный интерфейс (API), которая представляет собой набор функций приложение вызывает и служба поставщика интерфейса (SPI), которая представляет собой набор функций в драйвере реализованы. Это разделение не требуется, чтобы ODBC 3. *x*, которая использует **SQLFetchScroll**, bealigned стандартам и также должен соответствовать ODBC 2. *x*, которая использует **SQLExtendedFetch**.  
  
 ODBC 3*.x* API, который является набор функций приложение вызывает функцию, включает **SQLFetchScroll** и связанных с ними атрибуты инструкции. ODBC 3*.x* SPI, которая представляет собой набор функций, драйвер реализует, включает в себя **SQLFetchScroll**, **SQLExtendedFetch**и связанных с ними атрибуты инструкции. Поскольку ODBC не поддерживает это разделение между API и SPI формально, то возможна ODBC 3*.x* приложения, вызывающие **SQLExtendedFetch** и связанных с ними атрибуты инструкции. Тем не менее, нет причин для ODBC 3*.x* приложения для этого. Дополнительные сведения об API-интерфейсы и SPI см. во введении к [архитектура ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Дополнительные сведения о какие функции и инструкции атрибутов ODBC 3. *x* приложения следует использовать с блока и Прокручиваемые курсоры см. в разделе [блочных курсоров, Прокручиваемые курсоры и обратная совместимость для приложений ODBC 3.x](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Функции диспетчера драйверов](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)  
  
-   [Функции драйвера](../../../odbc/reference/appendixes/what-the-driver-does.md)
