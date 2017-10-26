---
title: "Приложение ж драйвер рекомендации для обеспечения обратной совместимости | Документы Microsoft"
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
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 911cd335-f2c0-4d03-9739-1078308a678a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e326abbc0a10899028bf93d27f219fadd8d7dd29
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="appendix-g-driver-guidelines-for-backward-compatibility"></a>Приложение ж драйвер рекомендации для обеспечения обратной совместимости
В этом приложении сведения для модулей записи драйвера, работа в ODBC 3. *x* драйверы, которые должны поддерживать ODBC 2.* x* приложений. Дополнительные сведения об обратной совместимости см. в разделе [обратной совместимости и соответствия стандартам](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Блочные курсоры, Прокручиваемые курсоры и обратная совместимость для драйверов ODBC 3.x](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) — новые функции, функции, которые существуют в ODBC 3.* x* , а не в ODBC 2.* x*. ODBC 3. *x* драйверы обычно не нужно беспокоиться об обратной совместимости с новыми функциями, так как ODBC 2.* x* приложения никогда не использовать их. Единственным исключением являются функции, относящиеся к **SQLFetch**, **SQLFetchScroll**, **SQLSetPos**, и **SQLExtendedFetch**; для получения дополнительных сведений сведения, см. ниже в этом приложении.  
  
-   [Сопоставление функций, не рекомендуется](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) — повторяющийся необходимы функциональные возможности, которые по-разному реализованы в ODBC 3.* x* и ODBC 2.* x*. ODBC 3. *x* драйверы не нужно беспокоиться об обратной совместимости с функциями повторяющихся потому, что диспетчер драйверов всегда сопоставляется ODBC 2.* x* функции ODBC 3.* x* функций при вызове ODBC 3.* x* драйвера. Таким образом ODBC 3. *x* драйвер видит только ODBC 3.* x* функции. Дополнительные сведения об этих сопоставлениях см ниже в этом приложении.  
  
-   [Изменения поведения и драйверы ODBC 3.x](../../../odbc/reference/appendixes/behavioral-changes-and-odbc-3-x-drivers.md) — изменения в поведении являются компонентами, которые обрабатываются по-разному в ODBC 3.* x* и ODBC 2.* x*. ODBC 3. *x* драйверы должны беспокоиться об изменениях в поведении и действовать в ответ на атрибута среды SQL_ATTR_ODBC_VERSION, установленный приложением.

