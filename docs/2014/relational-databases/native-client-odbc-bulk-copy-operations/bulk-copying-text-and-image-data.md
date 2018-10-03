---
title: Массовое копирование данных Text и Image | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: c468ec3cf52526192893458055cde857aeaa864d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103834"
---
# <a name="bulk-copying-text-and-image-data"></a>Массовое копирование данных text и image
  Большой **текст**, **ntext**, и **изображение** значения выполняются операции массового копирования с помощью [bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) функции. Код [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) для **текст**, **ntext**, или **изображение** столбец с *pData* указателя задано Значение NULL, указывающее, будут предоставлены данные **bcp_moretext**. Очень важно указать точную длину данных, предоставленных для каждого **текст**, **ntext**, или **изображение** столбца в каждой строке выполнено массовое копирование. Если длина данных для столбца отличается от длины столбца, указанной в [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md), использовать [bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) для задания длины на соответствующее значение. Объект [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) отправляет все отличного**текст**, отличных от-**ntext**и не-**изображение** данных; можно затем вызвать **bcp_moretext** для отправки **текст**, **ntext**, или **изображения** данные в отдельные блоки. Функции массового копирования определяют, что все данные отправлены для текущего **текст**, **ntext**, или **изображение** столбец, когда сумма длин данные посылались **bcp_moretext** равняется длине, указанной при последнем **bcp_collen** или **bcp_bind**.  
  
 **bcp_moretext** не имеет параметра для определения столбца. Если существует несколько **текст**, **ntext**, или **изображение** столбцов в строке, **bcp_moretext** оперирует **текст**, **ntext**, или **изображение** столбцов, начиная со столбца с наименьшим номером порядковый номер и Далее к столбцу с наибольшим порядковым номером. **bcp_moretext** переходит от одного столбца к другому, когда сумма длин данных, отправленных равняется длине, указанной при последнем **bcp_collen** или **bcp_bind** для текущего столбца.  
  
## <a name="see-also"></a>См. также  
 [Выполнение операций массового копирования &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)  
  
  
