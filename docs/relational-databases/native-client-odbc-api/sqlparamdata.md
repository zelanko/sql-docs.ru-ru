---
title: Метод SQLParamData | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLParamData function
ms.assetid: 92349482-ea22-4a6a-8484-e9c6566794fa
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 90034b01d0977df6f95f12434537fb4787fd56b7
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73786196"
---
# <a name="sqlparamdata"></a>SQLParamData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Когда метод SQLParamData возвращает *валуептрптр* , связанный с возвращающим табличное значение параметром, приложение должно вызвать SQLPutData с *StrLen_Or_Ind*. Если *StrLen_Or_Ind* имеет значение больше 0, это означает, что приложение готово к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственному клиенту для сбора данных параметров для следующей строки возвращающего табличные значения параметра. Если *StrLen_Or_Ind* имеет значение 0, значит, больше нет строк данных для возвращающего табличные значения параметра. Дополнительные сведения см. в разделе [Привязка и передача данных значений параметров и столбцов, возвращающих](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)табличное значение.  
  
 Дополнительные сведения о возвращающих табличное значение параметрах см. в разделе [возвращающие табличное значение параметры &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>См. также раздел  
 [Метод sqlparamdata](https://go.microsoft.com/fwlink/?LinkId=80706)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
