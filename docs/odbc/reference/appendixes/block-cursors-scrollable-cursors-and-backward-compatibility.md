---
title: Блочные курсоры, Прокручиваемые курсоры и обратная совместимость | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], backward compatibility
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- block cursors [ODBC]
ms.assetid: d9d271f6-d2d9-49b9-a365-4909ca06caae
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d3896473a1fa08f769f13d94bd1d81f373cf67c0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47854513"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility"></a>Блочные курсоры, прокручиваемые курсоры и обратная совместимость
Наличие обоих **SQLFetchScroll** и **SQLExtendedFetch** представляет сначала удалить разделить между прикладного программного интерфейса (API), которого представляет собой набор функций ODBC приложение вызывает и службу поставщика интерфейса (SPI), который представляет собой набор функций в драйвере реализованы. Это разделение необходим, чтобы ODBC 3. *x*, которая использует **SQLFetchScroll**, bealigned стандартам, а также быть совместим с ODBC 2. *x*, которая использует **SQLExtendedFetch**.  
  
 ODBC 3 *.x* API, который является набор функции приложение вызывает функцию, включает в себя **SQLFetchScroll** и связанные атрибуты инструкции. ODBC 3 *.x* SPI, которая представляет собой набор функций, драйвер реализует, включает в себя **SQLFetchScroll**, **SQLExtendedFetch**и связанные атрибуты инструкции. Поскольку ODBC не поддерживает это разделение между API и SPI формально, возможна ODBC 3 *.x* приложениям вызывать **SQLExtendedFetch** и связанные атрибуты инструкции. Тем не менее, нет причин для ODBC 3 *.x* приложения для этого. Дополнительные сведения об интерфейсах API и SPI см. во введении к [архитектура ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Сведения об какие функции и инструкции атрибутов ODBC 3. *x* приложения должны использовать блок и Прокручиваемые курсоры, см. в разделе [блочные курсоры, Прокручиваемые курсоры и обратная совместимость для приложений ODBC 3.x](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Функции диспетчера драйверов](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)  
  
-   [Функции драйвера](../../../odbc/reference/appendixes/what-the-driver-does.md)
