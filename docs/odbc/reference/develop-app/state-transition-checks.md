---
title: Контроль за переходом государства Документы Майкрософт
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
ms.openlocfilehash: 7dc1ddc126a2d652dfdb038cbb0e510f9735d7b0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299709"
---
# <a name="state-transition-checks"></a>Проверки переходов состояний
Менеджер драйвера проверяет, что состояние среды, соединения или оператора подходит для вызова функции. Например, подключение должно находиться в выделенном состоянии при вызове **S'LConnect;** заявление должно находиться в подготовленном состоянии, когда вызывается **S'LExecute.** Менеджер драйвера возвращает SQL_ERROR за ошибки перехода состояния.
