---
title: Усечение данных (службы SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- truncating data
- data truncation [Integration Services]
- expressions [Integration Services], data truncation
- truncate options [Integration Services]
ms.assetid: 02461e15-49ca-445b-abb3-5c369c283ec2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa36ccd8a161c15cf4d12d1f92bb1ec36b1ac0b2
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86920651"
---
# <a name="data-truncation-ssis"></a>Усечение данных (службы SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Преобразование значений из одного типа данных в другой может привести к их усечению.  
  
 Усечение может произойти в следующих случаях.  
  
-   Преобразование строковых данных из *DT_WSTR* в *DT_STR* той же длины, если исходная строка содержит двухбайтовые символы.  
  
-   Приведение целого числа из *DT_I4* в *DT_I2* — могут быть потеряны значащие цифры.  
  
-   Приведение целого числа без знака в целое число со знаком — могут быть потеряны значащие цифры.  
  
-   Приведение действительного числа из *DT_R8* в *DT_R4* — могут быть потеряны незначащие цифры.  
  
-   Приведение целого числа из *DT_I4* в *DT_R4* — могут быть потеряны незначащие цифры.  
  
 Средство оценки выражений определяет явные приведения, которые могут привести к усечению, и выдает предупреждение, если выражение прошло синтаксический анализ. Например, средство оценки выражений выдаст предупреждение, если строка, состоящая из 30 символов, будет преобразована в строку, состоящую из 20 символов.  
  
 Однако усечение не проверяется во время выполнения. Во время выполнения данные усекаются без предупреждения. Большинство адаптеров обработки данных и преобразований поддерживают сообщения об ошибках, которые позволяют обработать неправильно расположенные ошибочные строки.  
  
 Дополнительные сведения об обработке усечения данных см. в статье [Обработка ошибок в данных](../../integration-services/data-flow/error-handling-in-data.md).  
  
  
