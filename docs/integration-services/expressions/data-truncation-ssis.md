---
title: Усечение данных (службы SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- truncating data
- data truncation [Integration Services]
- expressions [Integration Services], data truncation
- truncate options [Integration Services]
ms.assetid: 02461e15-49ca-445b-abb3-5c369c283ec2
caps.latest.revision: 37
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6fd9e7c0c04df6f9cb6ec326d02e876c8847d2d6
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35334358"
---
# <a name="data-truncation-ssis"></a>Усечение данных (службы SSIS)
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
  
  
