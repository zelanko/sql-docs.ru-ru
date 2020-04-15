---
title: 'Приложение G: Руководящие принципы драйвера для обратной совместимости (ru) Документы Майкрософт'
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292404"
---
# <a name="appendix-g-driver-guidelines-for-backward-compatibility"></a>Приложение Ж. Рекомендации по обеспечению обратной совместимости с драйвером
Это приложение предоставляет информацию для авторов драйверов, работающих над ODBC 3. *x* драйверы, которые должны поддерживать ODBC 2. *x* приложений. Для получения дополнительной [информации](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)о обратной совместимости см.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Блок Cursors, Scrollable Cursors, и обратная совместимость для водителей ODBC 3.x](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) - Новые функции являются функциями, которые существуют в ODBC 3. *x* и не в ODBC 2. *x*. ODBC 3. *x* драйверы, как правило, не придется беспокоиться о обратной совместимости с новыми функциями, потому что ODBC 2. *приложения x* никогда ими не используют. Единственными исключениями из этого являются функции, связанные с **S'LFetch,** **S'LFetchScroll**, **S'LSetPos**, и **S'LExtendedFetch;** для получения дополнительной информации, см., позже в этом приложении.  
  
-   [Отображение развенченных функций](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) - Дублированные функции — это функции, которые по-разному реализованы в ODBC 3. *x* и ODBC 2. *x*. ODBC 3. *x* драйверам не придется беспокоиться о обратной совместимости с дублированными функциями, потому что менеджер драйверов всегда отображает ODBC 2. *x* функции для ODBC 3. *х* функции при вызове ODBC 3. *x* драйвер. Таким образом, ODBC 3. *x* драйвер видит только ODBC 3. *х* функции. Для получения дополнительной информации об этих карт, см.  
  
-   [Поведенческие изменения и ДРАЙВЕРы ODBC 3.x](../../../odbc/reference/appendixes/behavioral-changes-and-odbc-3-x-drivers.md) - Изменения поведения — это функции, которые обрабатываются по-разному в ODBC 3. *x* и ODBC 2. *x*. ODBC 3. *драйверам* должны беспокоиться об изменениях поведения и действовать в ответ на атрибут среды SQL_ATTR_ODBC_VERSION, установленный приложением.
