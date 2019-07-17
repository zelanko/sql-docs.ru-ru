---
title: Проверка общих ошибок | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- general error checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 0c9a3425-0a7c-48de-9ff6-73601c26283e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f6b7c37febee411571b8ac8316d3800912e35758
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68069920"
---
# <a name="general-error-checks"></a>Проверка общих ошибок
Диспетчер драйверов проверяет одна общая ошибка. Он всегда возвращает значение SQL_ERROR, при обнаружении следующей ошибки: Функция должна поддерживается драйвером.
