---
title: SQLRowCount | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLRowCount function
ms.assetid: 967ed3d4-3d31-4485-ac92-027076ebc829
author: rothja
ms.author: jroth
ms.openlocfilehash: 410023d960bad6dde1060a509cc1bf46f67d77cc
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85021707"
---
# <a name="sqlrowcount"></a>SQLRowCount
  Если массивы значений параметров привязаны к выполнению инструкции, функция `SQLRowCount` возвращает SQL_ERROR, если любая строка значений параметра создает условие ошибки при выполнении инструкции. Через аргумент *RowCountPtr* функции значение возвращено не будет.  
  
 Приложение может воспользоваться атрибутом инструкции SQL_ATTR_PARAMS_PROCESSED_PTR для получения количества параметров, обработанных до возникновения ошибки.  
  
 Кроме этого, приложение может использовать массив значений состояния, привязанный с помощью атрибута инструкции SQL_ATTR_PARAM_STATUS_PTR, для получения массива смещений вызвавших ошибку строк параметров. Чтобы выяснить действительное число обработанных строк, приложение может просмотреть этот массив.  
  
 При [!INCLUDE[tsql](../../includes/tsql-md.md)] выполнении инструкции INSERT, Update, DELETE или MERGE с предложением OUTPUT SQLRowCount не возвращает количество строк, затронутых до тех пор, пока не будут потреблены все строки результирующего набора, сформированного предложением OUTPUT. Чтобы сконсуме эти строки, вызовите SQLFetch или SQLFetchScroll. Склресултколс возвращает значение-1, пока не будут использованы все строки результатов. После того как SQLFetch или SQLFetchScroll возвращает SQL_NO_DATA, приложение должно вызвать SQLRowCount, чтобы определить число затронутых строк перед вызовом SQLMoreResults для перехода к следующему результату.  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLRowCount](https://go.microsoft.com/fwlink/?LinkId=59367)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
