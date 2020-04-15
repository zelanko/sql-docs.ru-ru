---
title: Связывание столбцов Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: c4407694-c8e1-4b0b-a39d-b007e6c3b54d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fca4cfb1455c91ca57f7b1769266e2040d6a3511
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301825"
---
# <a name="binding-columns"></a>Привязка столбцов
Данные, полученные из источника данных, возвращаются в приложение переменными, выделенными приложением для этой цели. Прежде чем это сделать, приложение должно связать или *связать*эти переменные с столбцов набора результатов; концептуально этот процесс является таким же, как привязка переменных приложения к параметрам оператора. Когда приложение связывает переменную с столбцом набора результатов, оно описывает эту переменную - адрес, тип данных и т.д. - к водителю. Драйвер хранит эту информацию в структуре, которую он поддерживает для этого оператора, и использует ее для возврата значения из столбца при извлечении строки.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Привязка столбцов результирующего набора](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [Использование SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
