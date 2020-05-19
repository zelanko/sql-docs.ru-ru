---
title: Копирование данных в виде текста и изображений | Документация Майкрософт
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 03d77ce1a4526cee78431def0251329111433aac
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705827"
---
# <a name="bulk-copying-text-and-image-data"></a>Массовое копирование данных text и image
  Значения типа Large **Text**, **ntext**и **Image** копируются с помощью функции [bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) . Код [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) для столбца **Text**, **ntext**или **Image** с указателем *pData* , имеющим значение null, что означает, что данные будут предоставлены в **bcp_moretext**. Важно указать точную длину данных, предоставляемых для каждого столбца типа **Text**, **ntext**или **Image** в каждой строке с массовым копированием. Если длина данных столбца отличается от длины столбца, указанного в [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md), используйте [bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) , чтобы задать для длины правильное значение. [Bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) отправляет все данные, не являющиеся**текстовыми**, не-**ntext**и не являющиеся**изображениями** ; Затем вызывается **bcp_moretext** для отправки данных типа **Text**, **ntext**или **Image** в отдельных единицах. Функции операций с массовым копированием определяют, что все данные были отправлены для текущего столбца **Text**, **ntext**или **Image** , если сумма длин данных, отправленных с помощью **bcp_moretext** , равна длине, указанной в последней **bcp_collen** или **bcp_bind**.  
  
 **bcp_moretext** не имеет параметра для задания столбца. Если в строке имеется несколько столбцов типа **Text**, **ntext**или **Image** , **bcp_moretext** работает с столбцами типа **Text**, **ntext**или **Image** , начиная с столбца с наименьшим порядковым номером и Переходя к столбцу с наибольшим порядковым номером. **bcp_moretext** переходит от одного столбца к другому, когда сумма значений длины отправленных данных равна длине, указанной в последней **bcp_collen** или **bcp_bind** для текущего столбца.  
  
## <a name="see-also"></a>См. также  
 [Выполнение операций с массовым копированием &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)  
  
  
