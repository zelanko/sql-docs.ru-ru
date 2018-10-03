---
title: SQLParamData | Документация Майкрософт
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
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 57b45032038f81fe6e2e15202db7b8c790ca4716
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47856922"
---
# <a name="sqlparamdata"></a>SQLParamData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  При возвращении SQLParamData *ValuePtrPtr* сопоставленный табличное значение параметра, приложение должно вызвать SQLPutData с *StrLen_Or_Ind*. Если *StrLen_Or_Ind* имеет значение больше 0, это означает, что приложение будет готово к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента для сбора данных параметр для следующей строки возвращающих табличные значения параметра. Если *StrLen_Or_Ind* имеет значение 0, оно означает, что есть больше нет строк данных для возвращающих табличные значения параметра. Дополнительные сведения см. в разделе [привязки и Data Transfer of Table-Valued параметры и значения столбцов](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Дополнительные сведения о возвращающих табличные значения параметров, см. в разделе [возвращающего табличное значение параметров &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [SQLParamData](http://go.microsoft.com/fwlink/?LinkId=80706)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
