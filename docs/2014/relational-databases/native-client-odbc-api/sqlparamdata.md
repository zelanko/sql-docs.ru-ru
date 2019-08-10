---
title: Метод SQLParamData | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLParamData function
ms.assetid: 92349482-ea22-4a6a-8484-e9c6566794fa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 79285523ec83d3f10ad6f23010a7f9a6398e5980
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68890111"
---
# <a name="sqlparamdata"></a>SQLParamData
  Когда метод SQLParamData возвращает *валуептрптр* , связанный с возвращающим табличное значение параметром, приложение должно вызвать SQLPutData с *StrLen_Or_Ind*. Если значение *StrLen_Or_Ind* больше 0, это означает, что приложение готово для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента, чтобы собрать данные параметров для следующей строки возвращающего табличные значения параметра. Если *StrLen_Or_Ind* имеет значение 0, значит, больше нет строк данных для возвращающего табличные значения параметра. Дополнительные сведения см. в разделе [Привязка и передача данных значений параметров и столбцов,](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)возвращающих табличное значение.  
  
 Дополнительные сведения о возвращающих табличное значение параметрах см. в разделе возвращающие табличное значение [Параметры &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Метод SQLParamData](/sql/odbc/reference/syntax/sqlparamdata-function)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
