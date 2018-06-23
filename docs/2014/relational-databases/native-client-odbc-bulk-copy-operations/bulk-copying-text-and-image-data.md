---
title: Массовое копирование данных Text и Image | Документы Microsoft
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
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c674c24b4000ada4651dfb44ed2d49e9fd5bde83
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095455"
---
# <a name="bulk-copying-text-and-image-data"></a>Массовое копирование данных text и image
  Большие **текст**, **ntext**, и **изображения** значения выполняются операции массового копирования с помощью [bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) функции. Кода [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) для **текст**, **ntext**, или **изображения** столбец с *pData* значение указателя Значение NULL, показывающее, будут предоставлены данные **bcp_moretext**. Важно указать точную длину данных, предоставленных для каждого **текст**, **ntext**, или **изображения** столбца в каждой строке операции массового копирования. Если длина данных для столбца отличается от длины столбца, указанного в [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md), используйте [bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) длина присваивается соответствующее значение. A [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) отправляет все отличного**текст**, не являющихся-**ntext**и не-**изображения** данных; можно затем вызвать **bcp_moretext** для отправки **текст**, **ntext**, или **изображения** данные в отдельных единиц. Функции массового копирования определяют, что все данные были переданы для текущего **текст**, **ntext**, или **изображения** столбца при отправке сумма длин данных через **bcp_moretext** равняется длине, указанной при последнем **bcp_collen** или **bcp_bind**.  
  
 **bcp_moretext** не имеет параметра для определения столбца. Если существует несколько **текст**, **ntext**, или **изображения** столбцов в строке, **bcp_moretext** оперирует **текста**, **ntext**, или **изображения** столбцов, начиная со столбца с наименьшим числом порядковый номер и Далее к столбцу с наибольшим порядковым номером. **bcp_moretext** переходит от одного столбца к другому, если сумма длин переданных данных равняется длине, указанной при последнем **bcp_collen** или **bcp_bind** для текущего столбца.  
  
## <a name="see-also"></a>См. также  
 [Выполнение операций массового копирования &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)  
  
  