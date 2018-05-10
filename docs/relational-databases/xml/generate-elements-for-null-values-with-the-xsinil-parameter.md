---
title: Создание элементов для значений NULL с помощью параметра XSINIL | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: xml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, null values
- null values [SQL Server], XML
- ELEMENTS directive
- XSINIL parameter
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6cce3b58cd219a35aac830c41d5151a76146bd99
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="generate-elements-for-null-values-with-the-xsinil-parameter"></a>Создание элементов для значений NULL с помощью параметра XSINIL
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Директива **ELEMENTS** формирует XML, в котором каждое значение в столбце соответствует элементу XML. Если этот значение в столбце имеет значение NULL, элемент не добавляется. Указав в директиве ELEMENTS необязательный параметр **XSINIL** , можно запросить, чтобы для значений NULL тоже создавались элементы. В этом случае атрибут **xsi:nil** этого элемента имеет значение TRUE для каждого значения NULL в столбце.  
  
## <a name="see-also"></a>См. также:  
 [Использование с RAW Mode для FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  
