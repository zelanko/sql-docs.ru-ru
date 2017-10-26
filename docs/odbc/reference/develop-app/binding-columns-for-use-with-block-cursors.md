---
title: "Привязка столбцов для использования с блочными курсорами | Документы Microsoft"
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
- column-wise binding [ODBC]
- row-wise binding [ODBC]
- result sets [ODBC], binding columns
- cursors [ODBC], block
- binding columns [ODBC]
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 231beede-cdfa-4e28-8b10-2760b983250f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fe8c88946d6602f77bc39ac03b280fcca99cb8de
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="binding-columns-for-use-with-block-cursors"></a>Привязка столбцов для использования с блочных курсоров
Поскольку блочные курсоры возвращают несколько строк, приложений, использующих их необходимо привязать массив переменных для каждого столбца, а не одной переменной. Эти массивы называются *буферы строк*. Ниже приведены два стиля привязки.  
  
-   Привязать массив для каждого столбца. Это называется *привязки на уровне столбца* так как каждая структура данных (array) содержит данные для одного столбца.  
  
-   Определение структуры для хранения данных для всей строки и привязать массив этих структур. Это называется *привязка* поскольку каждая структура данных содержит данные для одной строки.  
  
 Если приложение связывает один переменных столбцов, он вызывает **SQLBindCol** для привязки столбцов массивов. Единственным различием является переданные адреса массив адресов, адресов не одной переменной. Приложение устанавливает атрибут инструкции SQL_BIND_BY_COLUMN для указания того, он использует ли привязка на уровне столбца или на уровне строки. Следует ли использовать привязки на уровне столбца или на уровне строки заключается главным образом в приоритета приложения. Привязка на уровне строки могут более точно соответствуют макет данных приложения, в этом случае он обеспечивает лучшую производительность.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Привязка на уровне столбца](../../../odbc/reference/develop-app/column-wise-binding.md)  
  
-   [Привязка на уровне строки](../../../odbc/reference/develop-app/row-wise-binding.md)

