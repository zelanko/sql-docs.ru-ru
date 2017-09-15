---
title: "Привязка столбцов | Документы Microsoft"
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
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: c4407694-c8e1-4b0b-a39d-b007e6c3b54d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5903070b8918baa9734e5d188d90861322b57986
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="binding-columns"></a>Привязка столбцов
Данные, полученные из источника данных возвращается в приложение в переменных, которые приложения, выделенной для этой цели. Прежде чем это можно сделать, необходимо связать приложение, или *привязки*, эти переменные со столбцами результирующего набора; по существу, этот процесс является таким же, как привязка переменных приложения с параметрами инструкции. Если приложение связывает переменную, чтобы столбец результирующего набора, он описывает этой переменной — адрес, тип данных и так далее — к драйверу. Драйвер сохраняет эти сведения в структуре, он поддерживает для этого оператора и использует сведения, чтобы возвращать значение из столбца при выборке строки.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Столбцы привязки результирующего набора](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [С помощью SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
