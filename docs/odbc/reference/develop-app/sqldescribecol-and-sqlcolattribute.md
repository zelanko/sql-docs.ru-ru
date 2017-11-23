---
title: "SQLDescribeCol и SQLColAttribute | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLColAttribute function [ODBC], and SQLDescribeCol
- SQLDescribeCol function [ODBC], and SQLColAttribute
- result sets [ODBC], metadata
- retrieving result set meta data [ODBC]
- metadata [ODBC], result set
ms.assetid: c2ca442c-03a8-4e0f-9e67-b300bb15962f
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6044ca37e00d96c4a86fb5e9740ec6dfc824ca51
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqldescribecol-and-sqlcolattribute"></a>SQLDescribeCol и SQLColAttribute
**SQLDescribeCol** и **SQLColAttribute** получаются метаданные результирующего набора. Различие между этими двумя функциями состоит в том **SQLDescribeCol** всегда возвращает же пять (столбца имя, тип данных, точность, масштаб и допустимость значений NULL), при **SQLColAttribute** возвращает одну часть сведений, запрошенный приложением. Тем не менее **SQLColAttribute** может возвращать гораздо более эффективные средства выбора метаданных, включая учет регистра символов для столбца, отображения размера, возможность обновления и возможность поиска.  
  
 Многие приложения, особенно для отображения только данных, требуют только метаданные, возвращаемые функциями **SQLDescribeCol**. Для этих приложений, легче и быстрее использовать **SQLDescribeCol** чем **SQLColAttribute** , так как сведения, возвращаемые в рамках одного вызова. Другие приложения, особенно для обновления данных, требуются дополнительные метаданные, возвращаемые функциями **SQLColAttribute** и поэтому использовать обе функции. Кроме того **SQLColAttribute** поддерживает метаданные, относящиеся к драйверу; Дополнительные сведения см. в разделе [типов данных драйвера, дескрипторов типов, типов данных, типы диагностики и атрибуты](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Приложение может получить метаданные результирующего набора в любое время после инструкции подготовки или выполнения, и до курсора результирующим набор не будет закрыт. Только некоторые приложения требуют метаданные результирующего набора после подготовки инструкции и перед его выполнением. Если это возможно приложения будет ожидать получения метаданных до, после выполнения инструкции, так как некоторые источники данных не может возвращать метаданные для подготовленных инструкций, имитируя этой возможности в драйвере часто медленно процесс. Например, драйвер может создать ноль строк результирующего набора, заменив **ГДЕ** предложения **ВЫБЕРИТЕ** инструкция с предложением **WHERE 1 = 2** и выполнения Результирующая инструкция.  
  
 Метаданные часто ресурсоемкость извлечения из источника данных. По этой причине драйверы следует кэшировать все метаданные, они извлечь с сервера и оставить его для при условии, что курсор результирующим открыт. Кроме того приложения должны запрашивать только метаданные, которые абсолютно необходимы.
