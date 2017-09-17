---
title: "Загрузка по порядковому номеру | Документы Microsoft"
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
- backward compatibility [ODBC], loading by ordinal
- compatibility [ODBC], loading by ordinal
- loading by ordinal [ODBC]
ms.assetid: 337d90ab-68eb-4940-a2f3-f7d5693ee766
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ef22486a7cbd9932c90069f461b83358c2db8fd4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="loading-by-ordinal"></a>Загрузка по порядковому номеру
В ODBC 2. *x*, для повышения производительности процесса подключения может быть выполнена загрузка по порядковому номеру. ODBC 2. *x* драйвер экспортирует функцию фиктивный с порядковый номер 199; когда диспетчер драйверов обнаруживает его, он разрешается адресов функций ODBC по порядковому номеру, а не по имени. Эта функция по-прежнему поддерживается для ODBC 2. *x* драйверов, но не поддерживается для ODBC 3*.x* драйверы.
