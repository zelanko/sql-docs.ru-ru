---
title: "Состояние проверки перехода | Документы Microsoft"
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
- diagnostic information [ODBC], driver manager error checking
- state transition checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 0706db7d-e125-4845-a13a-7fe4308f7360
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9a6873114b5d15bdf9bfbac369dacaea712a0236
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="state-transition-checks"></a>Смена состояния проверки
Диспетчер драйверов проверяет, входит в среду, соединение или оператор подходит для вызываемой функции. Например, подключение должно быть в выделенных состояние при **SQLConnect** вызывается; оператор должен находиться в подготовленного состояние при **SQLExecute** вызывается. Диспетчер драйверов возвращает значение SQL_ERROR для ошибки перехода состояния.
