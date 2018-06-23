---
title: Граница vs. Отсутствует привязка столбцами Text и Image | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 001a15a0242159c98ea07163f708c9f67356c1a2
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2018
ms.locfileid: "35703025"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Граница vs. Несвязанный текст и столбцы изображений
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  При использовании серверных курсоров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента оптимизируется для запрещения передачи данных непривязанным **текст**, **ntext**, или **изображения** столбцы в время **SQLFetch** выполняется. **Текст**, **ntext**, или **изображения** данных не производится на сервере до проблемы с приложением [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) для столбец.  
  
 Многие приложения могут быть написаны таким образом, что не **текст**, **ntext**, или **изображения** данные отображаются при прокрутке пользователем вверх и вниз в курсоре. Когда пользователь выбирает строку, чтобы получить более подробные сведения, приложение может затем вызвать **SQLGetData** для получения **текст**, **ntext**, или **изображения** данные. Это предотвратит передачу **текст**, **ntext**, или **изображения** данные для строк, пользователь не выбрать и таким образом запретит передачу очень большой объемы данных.  
  
## <a name="see-also"></a>См. также  
 [Управление столбцами Text и Image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)   
 [Режимы работы курсоров](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
  
