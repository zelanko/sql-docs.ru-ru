---
title: SQLRowCount | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLRowCount function
ms.assetid: 967ed3d4-3d31-4485-ac92-027076ebc829
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ae4c2fa55f5975357d94eaecb2f92e9468fee98f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189510"
---
# <a name="sqlrowcount"></a>SQLRowCount
  Если для выполнения инструкции привязаны массивы значений параметров `SQLRowCount` возвращает SQL_ERROR, если значения параметров любой строке создает ошибку при выполнении инструкции. Через аргумент *RowCountPtr* функции значение возвращено не будет.  
  
 Приложение может воспользоваться атрибутом инструкции SQL_ATTR_PARAMS_PROCESSED_PTR для получения количества параметров, обработанных до возникновения ошибки.  
  
 Кроме этого, приложение может использовать массив значений состояния, привязанный с помощью атрибута инструкции SQL_ATTR_PARAM_STATUS_PTR, для получения массива смещений вызвавших ошибку строк параметров. Чтобы выяснить действительное число обработанных строк, приложение может просмотреть этот массив.  
  
 Когда [!INCLUDE[tsql](../../includes/tsql-md.md)] выполняется инструкция INSERT, UPDATE, DELETE или MERGE с предложением OUTPUT, то эта функция не возвращает число строк, затронутых, пока не будут обработаны все строки результирующего набора, формируемого предложение OUTPUT. К строкам эти строки осуществляется вызовом SQLFetch или SQLFetchScroll. SQLResultCols возвращает -1, пока не будут обработаны все результирующие строки. После SQLFetch или SQLFetchScroll вернет значение SQL_NO_DATA, приложение должно вызвать SQLRowCount, чтобы определить количество строк, затронутых перед вызовом SQLMoreResults перемещение к следующему результату.  
  
## <a name="see-also"></a>См. также  
 [Функция SQLRowCount](http://go.microsoft.com/fwlink/?LinkId=59367)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  