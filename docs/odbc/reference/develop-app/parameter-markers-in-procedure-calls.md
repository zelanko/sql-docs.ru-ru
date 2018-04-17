---
title: Маркеры параметров в вызове процедуры | Документы Microsoft
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
- SQL statements [ODBC], interoperability
- parameter markers [ODBC]
- interoperability of SQL statements [ODBC], parameter markers
ms.assetid: cda56f2b-6eec-4cbc-8dbb-36d8fa9f9216
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7d603c656e16cfc092d3c085092d427eb8a5c12e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="parameter-markers-in-procedure-calls"></a>Маркеры параметров в вызове процедуры
При вызове процедуры, которые принимают параметры, совместимые приложения должны использовать маркеры параметров вместо значений параметров literal. Некоторые источники данных не поддерживают использование значений литерала параметра в вызове процедуры. Дополнительные сведения о параметрах см. в разделе [параметров инструкции](../../../odbc/reference/develop-app/statement-parameters.md). Дополнительные сведения о вызове процедуры см. в разделе [вызовы процедур](../../../odbc/reference/develop-app/procedure-calls.md)далее в этом разделе.
