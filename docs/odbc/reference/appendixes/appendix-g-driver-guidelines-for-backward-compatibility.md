---
title: Приложение ж Рекомендации по драйверов для обеспечения обратной совместимости | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d78de7b3bd1d91351a4159847d6605e30cc1353d
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52516901"
---
# <a name="appendix-g-driver-guidelines-for-backward-compatibility"></a>Приложение ж Рекомендации по драйверов для обеспечения обратной совместимости
В этом приложении сведения для модулей записи драйвер, работа в ODBC 3. *x* драйверы, которые должны поддерживать ODBC 2. *x* приложений. Дополнительные сведения об обратной совместимости см. в разделе [обратной совместимости и соответствия стандартам](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Блочные курсоры, Прокручиваемые курсоры и обратная совместимость для драйверов ODBC 3.x](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) -новые возможности, функции, которые существуют в ODBC 3. *x* , а не в ODBC 2. *x*. ODBC 3. *x* драйверы обычно не нужно беспокоиться об обратной совместимости с новыми функциями, так как ODBC 2. *x* никогда не использующих их приложений. Единственным исключением являются функции, относящиеся к **SQLFetch**, **SQLFetchScroll**, **SQLSetPos**, и **SQLExtendedFetch**; Дополнительные сведения сведения см. Далее в этом приложении.  
  
-   [Рекомендуется использовать функции сопоставления](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) -повторяющийся функции являются компонентами, которые реализуются по-разному в ODBC 3. *x* и ODBC 2. *x*. ODBC 3. *x* драйверы, не нужно беспокоиться об обратной совместимости с повторяющийся функции, потому что диспетчер драйверов всегда отображается ODBC 2. *x* функции ODBC 3. *x* функции при вызове ODBC 3. *x* драйвера. Таким образом ODBC 3. *x* драйвер видит только ODBC 3. *x* функции. Дополнительные сведения об этих сопоставлениях см. Далее в этом приложении.  
  
-   [Изменения в поведении и драйверы ODBC 3.x](../../../odbc/reference/appendixes/behavioral-changes-and-odbc-3-x-drivers.md) -изменения в поведении являются компонентами, которые обрабатываются по-разному в ODBC 3. *x* и ODBC 2. *x*. ODBC 3. *x* драйверы должны беспокоиться об изменениях в поведении и действовать в ответ на атрибуте среды SQL_ATTR_ODBC_VERSION, установленный приложением.
