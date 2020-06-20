---
title: Метаданные возвращающего табличное значение параметра для подготовленных инструкций | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), metadata for prepared statements
ms.assetid: fd2fc705-2e98-4011-9822-c7e6cca4a535
author: rothja
ms.author: jroth
ms.openlocfilehash: ad1394bd5e5bedc69a98308ba67a98434559c146
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "84998904"
---
# <a name="table-valued-parameter-metadata-for-prepared-statements"></a>Метаданные возвращающего табличное значение параметра для подготовленных инструкций
  Приложение может получать метаданные для вызова подготовленной процедуры через SQLNumParams и SQLDescribeParam. Для возвращающих табличные значения параметров *дататипептр* имеет значение SQL_SS_TABLE. Дополнительные метаданные доступны через SQLGetDescField для SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME и SQL_CA_SS_SCHEMA_NAME.  
  
 SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME и SQL_CA_SS_SCHEMA_NAME можно использовать с SQLColumns для получения метаданных столбца для табличных типов, связанных с параметрами, возвращающими табличное значение. В этом случае SQL_SOPT_SS_NAME_SCOPE должно быть установлено в SQL_SS_NAME_SCOPE_TABLE_TYPE перед вызовом SQLColumns. После получения метаданных столбца, соответствующего возвращающему табличное значение параметру, параметр SQL_SOPT_SS_NAME_SCOPE необходимо установить обратно в значение по умолчанию — SQL_SS_NAME_SCOPE_TABLE.  
  
 Параметры SQL_CA_SS_TYPE_NAME, SQL_CA_SS_TYPE_CATALOG_NAME и SQL_CA_SS_TYPE_SCHEMA_NAME также могут использоваться с параметрами определяемых пользователем типов данных CLR.  
  
 Для подготовленных инструкций, не являющихся вызовами хранимых процедур, нельзя получить метаданные возвращающего табличные значения параметра. При попытке выполнения данного действия приложение возвращает ошибку SQL_ERROR с кодом SQLSTATE 42000 и сообщение «Синтаксическая ошибка или нарушение доступа».  
  
## <a name="see-also"></a>См. также:  
 [Возвращающие табличное значение параметры &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
