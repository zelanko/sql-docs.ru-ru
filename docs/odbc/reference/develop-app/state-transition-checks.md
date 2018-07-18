---
title: Состояние проверки перехода | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- state transition checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 0706db7d-e125-4845-a13a-7fe4308f7360
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23f2b87fc943535075e1456bb31366ff9667b07b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910629"
---
# <a name="state-transition-checks"></a>Смена состояния проверки
Диспетчер драйверов проверяет, входит в среду, соединение или оператор подходит для вызываемой функции. Например, подключение должно быть в выделенных состояние при **SQLConnect** вызывается; оператор должен находиться в подготовленного состояние при **SQLExecute** вызывается. Диспетчер драйверов возвращает значение SQL_ERROR для ошибки перехода состояния.
