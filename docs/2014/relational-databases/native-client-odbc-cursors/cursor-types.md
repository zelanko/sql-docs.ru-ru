---
title: Типы курсоров | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- cursors [ODBC], types
- ODBC cursors, types
ms.assetid: 3a916cc7-f352-42cb-8b83-f78e06cef991
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e63cceadf80da13956ea576db50459279a251b51
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36110147"
---
# <a name="cursor-types"></a>Типы курсоров
  ODBC определяет четыре типа курсоров, поддерживаемых Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента. Эти курсоры различаются по способности обнаруживать изменения в результирующем наборе и в ресурсах, они используют, например памяти и пространству в **tempdb**. Курсор может обнаружить изменения в строках только при попытках повторной выборки этих данных; не существует способа для источника данных известить курсор об изменениях в текущих выбранных строках. На способность курсора обнаруживать изменения, которые не были внесены через курсор, также влияет уровень изоляции транзакций.  
  
 Существует четыре типа курсоров ODBC, поддерживаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Однопроходные курсоры не поддерживают прокрутку, они поддерживают только последовательную выборку строк от начала курсора до его конца.  
  
-   Статические курсоры встраиваются **tempdb** при открытии курсора. Они всегда отображают результирующий набор точно в том виде, в котором он был при открытии курсора. Они никогда не отражают изменения в данных. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] статические курсоры всегда доступны только для чтения. Так как статический серверный курсор построен как рабочая таблица в **tempdb**, размер результирующего набора не может превышать максимальный размер строки запрещаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Курсоры, управляемые набором ключей, имеют членство и порядок строк в результирующем наборе, установленные при открытии курсора. Изменения в неключевых столбцах видимы через курсор.  
  
-   Динамические курсоры — это противоположность статических курсоров. Динамические курсоры отражают все изменения строк в результирующем наборе. Значения типа данных, порядок и членство строк в результирующем наборе могут меняться для каждой выборки.  
  
## <a name="see-also"></a>См. также  
 [Использование курсоров &#40;ODBC&#41;](using-cursors-odbc.md)  
  
  