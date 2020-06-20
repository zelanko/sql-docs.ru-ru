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
author: rothja
ms.author: jroth
ms.openlocfilehash: a4e0e8b31a65f28ce83e0d114231bdedd7a35a4c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85021966"
---
# <a name="sqlparamdata"></a>SQLParamData
  Когда метод SQLParamData возвращает *валуептрптр* , связанный с возвращающим табличное значение параметром, приложение должно вызвать SQLPutData с *StrLen_Or_Ind*. Если *StrLen_Or_Ind* имеет значение больше 0, это означает, что приложение готово для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента, чтобы собрать данные параметров для следующей строки возвращающего табличные значения параметра. Если *StrLen_Or_Ind* имеет значение 0, значит, больше нет строк данных для возвращающего табличные значения параметра. Дополнительные сведения см. в разделе [Привязка и передача данных значений параметров и столбцов, возвращающих](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)табличное значение.  
  
 Дополнительные сведения о возвращающих табличное значение параметрах см. в разделе [возвращающие табличное значение параметры &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод SQLParamData](/sql/odbc/reference/syntax/sqlparamdata-function)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
