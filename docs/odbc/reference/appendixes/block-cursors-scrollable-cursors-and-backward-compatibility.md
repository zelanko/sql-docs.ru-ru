---
title: Блок Cursors, Прокрутки Курсоры, и обратной совместимости (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe24362f1a49577a7fb494f768947080d0ab6e9e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292314"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility"></a>Блочные курсоры, прокручиваемые курсоры и обратная совместимость
Существование как **S'LFetchScroll,** так и **S'LExtendedFetch** представляет собой первый четкий раскол в ODBC между интерфейсом прикладного программирования (API), который представляет собой набор функций, которые вызывает приложение, и интерфейсом поставщика услуг (SPI), который является набором функций, реализуемых драйвером. Этот раскол необходим для того, чтобы ODBC *3.x*, который использует **S'LFetchScroll**, быть совместимым со стандартами, а также быть совместимым с ODBC *2.x*, который использует **S'LExtendedFetch**.  
  
 API ODBC *3.x,* который представляет собой набор функций, которые вызывает приложение, включает в себя **S'LFetchScroll** и связанные с ними атрибуты оператора. ODBC *3.x* SPI, который представляет собой набор функций, реализуемых драйвером, включает в себя **S'LFetchScroll**, **S'LExtendedFetch**, и связанные атрибуты оператора. Поскольку ODBC формально не обеспечивает соблюдение этого разделения между API и SPI, приложения ODBC *3.x* могут вызывать **s'LExtendedFetch** и связанные с ними атрибуты оператора. Тем не менее, нет никаких оснований для приложения ODBC *3.x,* чтобы сделать это. Для получения дополнительной информации об AI [ODBC Architecture](../../../odbc/reference/odbc-architecture.md)и SPI см.  
  
 Для получения информации о том, какие функции и выписки атрибуты ODBC *3.x* приложение должно использоваться с блоком и прокрутки [курсоры, см. Блок Курсоры, Scrollable Cursors, и обратной совместимости для ODBC 3.x приложений](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Функции диспетчера драйверов](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)  
  
-   [Функции драйвера](../../../odbc/reference/appendixes/what-the-driver-does.md)
