---
title: Проверки смены состояния | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107281"
---
# <a name="state-transition-checks"></a>Проверки переходов состояний
Диспетчер драйверов проверяет, подходит ли состояние среды, соединения или инструкции для вызова вызываемой функции. Например, соединение должно находиться в выделенном состоянии при вызове **SQLConnect** ; Инструкция должна быть в подготовленном состоянии при вызове **SQLExecute** . Диспетчер драйверов возвращает SQL_ERROR для ошибок перехода состояния.
