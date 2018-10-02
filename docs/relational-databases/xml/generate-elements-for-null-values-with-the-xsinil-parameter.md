---
title: Создание элементов для значений NULL с помощью параметра XSINIL | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, null values
- null values [SQL Server], XML
- ELEMENTS directive
- XSINIL parameter
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 66086f046b4ea95325747131edcea5f8868e1562
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47702482"
---
# <a name="generate-elements-for-null-values-with-the-xsinil-parameter"></a>Создание элементов для значений NULL с помощью параметра XSINIL
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Директива **ELEMENTS** формирует XML, в котором каждое значение в столбце соответствует элементу XML. Если этот значение в столбце имеет значение NULL, элемент не добавляется. Указав в директиве ELEMENTS необязательный параметр **XSINIL** , можно запросить, чтобы для значений NULL тоже создавались элементы. В этом случае атрибут **xsi:nil** этого элемента имеет значение TRUE для каждого значения NULL в столбце.  
  
## <a name="see-also"></a>См. также:  
 [Использование с RAW Mode для FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  
