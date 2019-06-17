---
title: Состояние проверки переходов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- state transition checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 0706db7d-e125-4845-a13a-7fe4308f7360
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dcfefffb167b97ace09bfa358296d886265a987f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149065"
---
# <a name="state-transition-checks"></a>Проверки переходов состояний
Диспетчер драйверов проверяет, что состояние среды, подключения или инструкция подходит для вызываемой функции. Например, подключение должно быть в выделенный состояние при **SQLConnect** вызывается; инструкция должна быть в подготовленную состояние при **SQLExecute** вызывается. Диспетчер драйверов возвращает ошибку SQL_ERROR для ошибки перехода состояния.
