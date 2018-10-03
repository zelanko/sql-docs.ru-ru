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
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47809632"
---
# <a name="state-transition-checks"></a>Проверки переходов состояний
Диспетчер драйверов проверяет, что состояние среды, подключения или инструкция подходит для вызываемой функции. Например, подключение должно быть в выделенный состояние при **SQLConnect** вызывается; инструкция должна быть в подготовленную состояние при **SQLExecute** вызывается. Диспетчер драйверов возвращает ошибку SQL_ERROR для ошибки перехода состояния.
