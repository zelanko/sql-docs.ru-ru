---
title: Загрузка по порядковому номеру | Документы Microsoft
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
- backward compatibility [ODBC], loading by ordinal
- compatibility [ODBC], loading by ordinal
- loading by ordinal [ODBC]
ms.assetid: 337d90ab-68eb-4940-a2f3-f7d5693ee766
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e37cd9754b402960ca12b0dbdbeaf43a5f2aee61
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32906249"
---
# <a name="loading-by-ordinal"></a>Загрузка по порядковому номеру
В ODBC 2. *x*, для повышения производительности процесса подключения может быть выполнена загрузка по порядковому номеру. ODBC 2. *x* драйвер экспортирует функцию фиктивный с порядковый номер 199; когда диспетчер драйверов обнаруживает его, он разрешается адресов функций ODBC по порядковому номеру, а не по имени. Эта функция по-прежнему поддерживается для ODBC 2. *x* драйверов, но не поддерживается для ODBC 3 *.x* драйверы.
