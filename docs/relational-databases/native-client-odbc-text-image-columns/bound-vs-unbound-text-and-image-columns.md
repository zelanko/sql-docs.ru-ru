---
title: Связанные и несвязанные столбцы text и Image | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: ffd3442e-d880-46e9-b848-2365a09a2406
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d23b999c40aaa6a7cd8200185f18f14ac759403f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73778869"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Привязанные и непривязанные столбцы типа Text и Image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  При использовании серверных курсоров драйвер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC для собственного клиента оптимизирован для передачи данных для непривязанных столбцов типа **Text**, **ntext**или **Image** во время выполнения **SQLFetch** . Данные типа **Text**, **ntext**или **Image** на самом деле не извлекаются с сервера, пока приложение не выдаст [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) для столбца.  
  
 Многие приложения могут быть написаны таким образом, чтобы не отображались данные типа **Text**, **ntext**или **Image** , пока пользователь просто прокручивается вверх и вниз в курсоре. Когда пользователь выбирает строку для получения более подробной информации, приложение может вызвать **SQLGetData** для получения данных типа **Text**, **ntext**или **Image** . Это предотвратит передачу данных типа **Text**, **ntext**или **Image** для любых строк, которые пользователь не выбирает, и таким образом предотвращает передачу очень больших объемов данных.  
  
## <a name="see-also"></a>См. также:  
 [Управление столбцами Text и Image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)   
 [Режимы работы курсоров](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
  
