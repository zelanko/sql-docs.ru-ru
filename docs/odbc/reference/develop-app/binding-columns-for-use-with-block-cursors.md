---
title: Привязка столбцов для использования с блочными курсорами | Документы Microsoft
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
manager: craigg
ms.openlocfilehash: f9bee14abc4bbdbad17360666d40a7d59af5480d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909649"
---
# <a name="binding-columns-for-use-with-block-cursors"></a>Привязка столбцов для использования с блочных курсоров
Поскольку блочные курсоры возвращают несколько строк, приложений, использующих их необходимо привязать массив переменных для каждого столбца, а не одной переменной. Эти массивы называются *буферы строк*. Ниже приведены два стиля привязки.  
  
-   Привязать массив для каждого столбца. Это называется *привязки на уровне столбца* так как каждая структура данных (array) содержит данные для одного столбца.  
  
-   Определение структуры для хранения данных для всей строки и привязать массив этих структур. Это называется *привязка* поскольку каждая структура данных содержит данные для одной строки.  
  
 Если приложение связывает один переменных столбцов, он вызывает **SQLBindCol** для привязки столбцов массивов. Единственным различием является переданные адреса массив адресов, адресов не одной переменной. Приложение устанавливает атрибут инструкции SQL_BIND_BY_COLUMN для указания того, он использует ли привязка на уровне столбца или на уровне строки. Следует ли использовать привязки на уровне столбца или на уровне строки заключается главным образом в приоритета приложения. Привязка на уровне строки могут более точно соответствуют макет данных приложения, в этом случае он обеспечивает лучшую производительность.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Привязка на уровне столбца](../../../odbc/reference/develop-app/column-wise-binding.md)  
  
-   [Привязка на уровне строки](../../../odbc/reference/develop-app/row-wise-binding.md)
