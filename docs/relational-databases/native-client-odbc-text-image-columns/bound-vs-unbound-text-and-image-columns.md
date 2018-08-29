---
title: Привязанные и Несвязанных столбцами Text и Image | Документация Майкрософт
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
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8439982e197354dc786a82ea627500975d870f3c
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43091107"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Привязанные и непривязанные столбцы text и image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  При использовании серверных курсоров, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента оптимизирован для запрещения передачи данных непривязанным **текст**, **ntext**, или **образа** на столбцы время **SQLFetch** выполняется. **Текст**, **ntext**, или **изображение** данных не производится на сервере до проблем приложений [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) для столбец.  
  
 Многие приложения могут быть написаны таким образом, чтобы не **текст**, **ntext**, или **изображения** данные отображаются при прокрутке пользователем вверх и вниз в курсоре. Когда пользователь выбирает строку, чтобы получить более подробные сведения, приложение может затем вызвать **SQLGetData** извлекаемого **текст**, **ntext**, или **изображение** данные. Это предотвратит передачу **текст**, **ntext**, или **изображения** данные для строк, пользователь не выберите и таким образом запретит передачу очень больших объемы данных.  
  
## <a name="see-also"></a>См. также  
 [Управление столбцами Text и Image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)   
 [Режимы работы курсоров](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
  
