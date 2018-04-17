---
title: Загрузка по порядковому номеру | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- backward compatibility [ODBC], loading by ordinal
- compatibility [ODBC], loading by ordinal
- loading by ordinal [ODBC]
ms.assetid: 337d90ab-68eb-4940-a2f3-f7d5693ee766
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 33b538dcba0898e11d84920e9b6153da165200d0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="loading-by-ordinal"></a>Загрузка по порядковому номеру
В ODBC 2. *x*, для повышения производительности процесса подключения может быть выполнена загрузка по порядковому номеру. ODBC 2. *x* драйвер экспортирует функцию фиктивный с порядковый номер 199; когда диспетчер драйверов обнаруживает его, он разрешается адресов функций ODBC по порядковому номеру, а не по имени. Эта функция по-прежнему поддерживается для ODBC 2. *x* драйверов, но не поддерживается для ODBC 3*.x* драйверы.
