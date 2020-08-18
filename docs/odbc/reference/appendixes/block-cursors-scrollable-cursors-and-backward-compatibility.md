---
description: Блочные курсоры, прокручиваемые курсоры и обратная совместимость
title: Блочные курсоры, прокручиваемые курсоры и обратная совместимость | Документация Майкрософт
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
ms.openlocfilehash: 46f6d3611b0a55325387f2c7723734500d48af83
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88411300"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility"></a>Блочные курсоры, прокручиваемые курсоры и обратная совместимость
Существование обеих **SQLFetchScroll** и **SQLExtendedFetch** представляет собой первое четкое разделение в ODBC между интерфейсом прикладного программирования (API), который представляет собой набор функций, которые вызывает приложение, и интерфейс поставщика услуг (SPI), который представляет собой набор функций, реализуемых драйвером. Это разбиение необходимо для того, чтобы ODBC *3. x*, использующий **SQLFetchScroll**, совпадал с стандартами, а также быть совместимым с ODBC *2. x*, который использует **SQLExtendedFetch**.  
  
 API ODBC *3. x* , который представляет собой набор функций, которые вызывает приложение, содержит **SQLFetchScroll** и связанные с ним атрибуты инструкции. Параметр SPI ODBC *3. x* , который представляет собой набор функций, реализуемых драйвером, включает **SQLFetchScroll**, **SQLExtendedFetch**и связанные атрибуты инструкции. Так как ODBC не обеспечивает такую раздельную разбивку между API и SPI, приложения ODBC *3. x* могут вызывать **SQLExtendedFetch** и связанные с ними атрибуты инструкции. Однако для этого нет причин для приложения ODBC *3. x* . Дополнительные сведения об интерфейсах API и спис см. в статье Введение в [архитектуру ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Сведения о функциях и атрибутах инструкций, которые приложение ODBC *3. x* должно использовать с блоками и прокручиваемыми курсорами, см. в разделе [блочные курсоры, прокручиваемые курсоры и обратная совместимость приложений ODBC 3. x](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Функции диспетчера драйверов](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)  
  
-   [Функции драйвера](../../../odbc/reference/appendixes/what-the-driver-does.md)
