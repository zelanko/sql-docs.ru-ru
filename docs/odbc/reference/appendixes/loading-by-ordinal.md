---
title: Загрузка по порядковому номеру | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], loading by ordinal
- compatibility [ODBC], loading by ordinal
- loading by ordinal [ODBC]
ms.assetid: 337d90ab-68eb-4940-a2f3-f7d5693ee766
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 702e1fe58080cc370ab9a858c985a7744df85050
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181329"
---
# <a name="loading-by-ordinal"></a>Загрузка по порядковому номеру
В ODBC 2. *x*, чтобы повысить производительность процесса подключения может быть выполнена загрузка по порядковому номеру. ODBC 2. *x* драйвер экспортирует функцию фиктивный с 199 порядкового номера; когда диспетчер драйверов обнаруживает его, он разрешает адресов функций ODBC, по порядковому номеру, а не по имени. Эта функция по-прежнему поддерживается для ODBC 2. *x* драйверов, но не поддерживается для ODBC 3 *.x* драйверы.
