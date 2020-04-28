---
title: Приложение ж. рекомендации по использованию драйверов для обратной совместимости | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 911cd335-f2c0-4d03-9739-1078308a678a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1055f94cb54bba9262f210e5df5f028029aebf5b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292404"
---
# <a name="appendix-g-driver-guidelines-for-backward-compatibility"></a>Приложение Ж. Рекомендации по обеспечению обратной совместимости с драйвером
В этом приложении содержатся сведения о модулях записи драйверов, работающих с ODBC 3. *x* драйверов, требующих поддержки ODBC 2. приложения *x* . Дополнительные сведения о обратной совместимости см. в разделе [обратная совместимость и соответствие стандартам](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Блочные курсоры, прокручиваемые курсоры и обратная совместимость для драйверов ODBC 3. x.](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) новые функции — это функции, существующие в ODBC 3. *x* , а не в ODBC 2. *x*. ODBC 3. драйверам *x* обычно не нужно беспокоиться о обратной совместимости с новыми функциями, поскольку ODBC 2. приложения *x* никогда не используют их. Единственными исключениями из этого являются функции, связанные с **SQLFetch**, **SQLFetchScroll**, **SQLSetPos**и **SQLExtendedFetch**; Дополнительные сведения см. в подразделе далее в этом приложении.  
  
-   [Сопоставление устаревших функций](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) — дублирование компонентов — это функции, которые реализуются по-РАЗНОМУ в ODBC 3. *x* и ODBC 2. *x*. ODBC 3. драйверам *x* не нужно беспокоиться о обратной совместимости с повторяющимися компонентами, так как диспетчер драйверов всегда сопоставляет ODBC 2. функции *x* для ODBC 3. функции *x* при вызове ODBC 3. драйвер *x* . Таким же примером является ODBC 3. драйвер *x* видит только ODBC 3. функции *x* . Дополнительные сведения об этих сопоставлениях см. в подразделе далее в этом приложении.  
  
-   [Изменения в поведении и драйверы ODBC 3. x](../../../odbc/reference/appendixes/behavioral-changes-and-odbc-3-x-drivers.md) — изменения в поведении — это функции, которые обрабатываются иначе в ODBC 3. *x* и ODBC 2. *x*. ODBC 3. драйверы *x* должны беспокоиться об изменениях в поведении и действовать в ответ на атрибут среды SQL_ATTR_ODBC_VERSION, заданный приложением.
