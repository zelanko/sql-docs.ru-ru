---
description: Проверки переходов состояний
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 50a845f2b83ada7c9d4f03f252b6d2bc3d3eff3d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476376"
---
# <a name="state-transition-checks"></a>Проверки переходов состояний
Диспетчер драйверов проверяет, подходит ли состояние среды, соединения или инструкции для вызова вызываемой функции. Например, соединение должно находиться в выделенном состоянии при вызове **SQLConnect** ; Инструкция должна быть в подготовленном состоянии при вызове **SQLExecute** . Диспетчер драйверов возвращает SQL_ERROR для ошибок перехода состояния.
