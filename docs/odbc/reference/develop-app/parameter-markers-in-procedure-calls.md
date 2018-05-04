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
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- parameter markers [ODBC]
- interoperability of SQL statements [ODBC], parameter markers
ms.assetid: cda56f2b-6eec-4cbc-8dbb-36d8fa9f9216
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 744c9d8a7c75df66439794f1b461112800094ba7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="parameter-markers-in-procedure-calls"></a>Маркеры параметров в вызове процедуры
При вызове процедуры, которые принимают параметры, совместимые приложения должны использовать маркеры параметров вместо значений параметров literal. Некоторые источники данных не поддерживают использование значений литерала параметра в вызове процедуры. Дополнительные сведения о параметрах см. в разделе [параметров инструкции](../../../odbc/reference/develop-app/statement-parameters.md). Дополнительные сведения о вызове процедуры см. в разделе [вызовы процедур](../../../odbc/reference/develop-app/procedure-calls.md)далее в этом разделе.
