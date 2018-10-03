---
title: Массовое копирование данных Text и Image | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5032f6d038130fc78405949a171a39a6f0ec1842
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47607182"
---
# <a name="bulk-copying-text-and-image-data"></a>Массовое копирование данных text и image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Большой **текст**, **ntext**, и **изображение** значения выполняются операции массового копирования с помощью [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) функции. Код [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) для **текст**, **ntext**, или **изображение** столбец с *pData* указателя задано Значение NULL, указывающее, будут предоставлены данные **bcp_moretext**. Очень важно указать точную длину данных, предоставленных для каждого **текст**, **ntext**, или **изображение** столбца в каждой строке выполнено массовое копирование. Если длина данных для столбца отличается от длины столбца, указанной в [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md), использовать [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) для задания длины на соответствующее значение. Объект [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) отправляет все отличного**текст**, отличных от-**ntext**и не-**изображение** данных; можно затем вызвать **bcp_moretext** для отправки **текст**, **ntext**, или **изображения** данные в отдельные блоки. Функции массового копирования определяют, что все данные отправлены для текущего **текст**, **ntext**, или **изображение** столбец, когда сумма длин данные посылались **bcp_moretext** равняется длине, указанной при последнем **bcp_collen** или **bcp_bind**.  
  
 **bcp_moretext** не имеет параметра для определения столбца. Если существует несколько **текст**, **ntext**, или **изображение** столбцов в строке, **bcp_moretext** оперирует **текст**, **ntext**, или **изображение** столбцов, начиная со столбца с наименьшим номером порядковый номер и Далее к столбцу с наибольшим порядковым номером. **bcp_moretext** переходит от одного столбца к другому, когда сумма длин данных, отправленных равняется длине, указанной при последнем **bcp_collen** или **bcp_bind** для текущего столбца.  
  
## <a name="see-also"></a>См. также  
 [Выполнение операций массового копирования &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
