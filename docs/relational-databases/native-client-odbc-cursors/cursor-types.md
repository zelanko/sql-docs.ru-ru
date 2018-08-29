---
title: Типы курсоров | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- cursors [ODBC], types
- ODBC cursors, types
ms.assetid: 3a916cc7-f352-42cb-8b83-f78e06cef991
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 73df68beb5c6fa49ba4c096d73556d129f897f87
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43080677"
---
# <a name="cursor-types"></a>Типы курсоров
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC определяет четыре типа курсоров, поддерживаемых Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента. Эти курсоры различаются по способности обнаруживать изменения в результирующем наборе и в ресурсах, они используют, например памяти и пространству в **tempdb**. Курсор может обнаружить изменения в строках только при попытках повторной выборки этих данных; не существует способа для источника данных известить курсор об изменениях в текущих выбранных строках. На способность курсора обнаруживать изменения, которые не были внесены через курсор, также влияет уровень изоляции транзакций.  
  
 Существует четыре типа курсоров ODBC, поддерживаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Однопроходные курсоры не поддерживают прокрутку, они поддерживают только последовательную выборку строк от начала курсора до его конца.  
  
-   Статические курсоры встраиваются **tempdb** при открытии курсора. Они всегда отображают результирующий набор точно в том виде, в котором он был при открытии курсора. Они никогда не отражают изменения в данных. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] статические курсоры всегда доступны только для чтения. Так как статический серверный курсор построен как рабочая таблица в **tempdb**, размер результирующего набора не может превышать максимальный размер строки допускаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Курсоры, управляемые набором ключей, имеют членство и порядок строк в результирующем наборе, установленные при открытии курсора. Изменения в неключевых столбцах видимы через курсор.  
  
-   Динамические курсоры — это противоположность статических курсоров. Динамические курсоры отражают все изменения строк в результирующем наборе. Значения типа данных, порядок и членство строк в результирующем наборе могут меняться для каждой выборки.  
  
## <a name="see-also"></a>См. также  
 [Использование курсоров &#40;ODBC&#41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
