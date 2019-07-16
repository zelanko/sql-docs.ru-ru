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
ms.openlocfilehash: b337d317092ad6ae20cc91236d69c1314de96bce
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68107281"
---
# <a name="state-transition-checks"></a>Проверки переходов состояний
Диспетчер драйверов проверяет, что состояние среды, подключения или инструкция подходит для вызываемой функции. Например, подключение должно быть в выделенный состояние при **SQLConnect** вызывается; инструкция должна быть в подготовленную состояние при **SQLExecute** вызывается. Диспетчер драйверов возвращает ошибку SQL_ERROR для ошибки перехода состояния.
