---
title: Связанные против несвязанных текстовых и изображений столбцов (ru) Документы Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0cfa05f7019342d63ab6f3092c3b6df5ae6e8daa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297748"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Привязанные и непривязанные столбцы text и image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  При использовании курсоров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] серверов драйвер Native Client ODBC оптимизирован, чтобы не передавать данные для несвязанного **текста,** **ntext**или столбцов **изображений** во время выполнения **S'LFetch.** **Текст,** **ntext**или данные **изображения** фактически не извлекаются с сервера до тех пор, пока приложение не выдаст для столбца [s'LGetData.](../../relational-databases/native-client-odbc-api/sqlgetdata.md)  
  
 Многие приложения могут быть написаны так, что **текст,** **ntext**или данные **изображения** не отображается в то время как пользователь просто прокрутки вверх и вниз в курсоре. Когда пользователь выбирает строку, чтобы получить более подробную информацию, приложение может вызвать **S'LGetData,** чтобы получить **текст,** **ntext**или данные **изображения.** Это предотвратит передачу **текста,** **ntext**или данных **изображений** для любой из строк, которые пользователь не выберет, и, следовательно, может предотвратить передачу очень больших объемов данных.  
  
## <a name="see-also"></a>См. также:  
 [Управление текстовыми и имиджевыми столбцов](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)   
 [Режимы работы курсоров](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
  
