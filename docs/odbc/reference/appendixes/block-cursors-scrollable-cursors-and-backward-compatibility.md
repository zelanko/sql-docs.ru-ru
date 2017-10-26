---
title: "Блочные курсоры, Прокручиваемые курсоры и обратной совместимости | Документы Microsoft"
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
- scrollable cursors [ODBC]
- cursors [ODBC], backward compatibility
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- block cursors [ODBC]
ms.assetid: d9d271f6-d2d9-49b9-a365-4909ca06caae
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 72c256f326366d631dada13fbfe002c8d4674eda
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility"></a>Блочные курсоры, Прокручиваемые курсоры и обратная совместимость
На наличие **SQLFetchScroll** и **SQLExtendedFetch** представляет первый clear разбиения в ODBC между приложения программный интерфейс (API), которая представляет собой набор функций приложение вызывает и служба поставщика интерфейса (SPI), которая представляет собой набор функций в драйвере реализованы. Это разделение не требуется, чтобы ODBC 3. *x*, которая использует **SQLFetchScroll**, bealigned стандартам и также должен соответствовать ODBC 2.* x*, которая использует **SQLExtendedFetch**.  
  
 ODBC 3*.x* API, который является набор функций приложение вызывает функцию, включает **SQLFetchScroll** и связанных с ними атрибуты инструкции. ODBC 3*.x* SPI, которая представляет собой набор функций, драйвер реализует, включает в себя **SQLFetchScroll**, **SQLExtendedFetch**и связанных с ними атрибуты инструкции. Поскольку ODBC не поддерживает это разделение между API и SPI формально, то возможна ODBC 3*.x* приложения, вызывающие **SQLExtendedFetch** и связанных с ними атрибуты инструкции. Тем не менее, нет причин для ODBC 3*.x* приложения для этого. Дополнительные сведения об API-интерфейсы и SPI см. во введении к [архитектура ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Дополнительные сведения о какие функции и инструкции атрибутов ODBC 3. *x* приложения следует использовать с блока и Прокручиваемые курсоры см. в разделе [блочных курсоров, Прокручиваемые курсоры и обратная совместимость для приложений ODBC 3.x](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Назначение диспетчера драйверов](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)  
  
-   [Что делает драйвер](../../../odbc/reference/appendixes/what-the-driver-does.md)

