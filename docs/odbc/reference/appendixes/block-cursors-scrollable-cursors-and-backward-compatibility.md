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
ms.openlocfilehash: 66b4cf0ce2b2ffc15a9e450461021a9b20b1f0c3
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67794135"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility"></a>Блочные курсоры, прокручиваемые курсоры и обратная совместимость
Наличие обоих **SQLFetchScroll** и **SQLExtendedFetch** представляет сначала удалить разделить между прикладного программного интерфейса (API), которого представляет собой набор функций ODBC приложение вызывает и службу поставщика интерфейса (SPI), который представляет собой набор функций в драйвере реализованы. Это разделение необходим, чтобы ODBC *3.x*, которая использует **SQLFetchScroll**, bealigned стандартам, а также быть совместим с ODBC *2.x*, использующий **SQLExtendedFetch**.  
  
 ODBC *3.x* API, который является набор функции приложение вызывает функцию, включает в себя **SQLFetchScroll** и связанные атрибуты инструкции. ODBC *3.x* SPI, которая представляет собой набор функций, драйвер реализует, включает в себя **SQLFetchScroll**, **SQLExtendedFetch**и связанные атрибуты инструкции. Поскольку ODBC не поддерживает это разделение между API и SPI формально, это возможно для ODBC *3.x* приложениям вызывать **SQLExtendedFetch** и связанные атрибуты инструкции. Тем не менее, нет причин для ODBC *3.x* приложения для этого. Дополнительные сведения об интерфейсах API и SPI см. во введении к [архитектура ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Для сведения об какие функции и инструкции атрибуты ODBC *3.x* приложения должны использовать блок и Прокручиваемые курсоры, см. в разделе [блочные курсоры, Прокручиваемые курсоры и обратная совместимость для ODBC 3.x Приложения](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Функции диспетчера драйверов](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)  
  
-   [Функции драйвера](../../../odbc/reference/appendixes/what-the-driver-does.md)
