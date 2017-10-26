---
title: "Автоматическое заполнение IPD | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automatically populating ipd [ODBC]
- descriptors [ODBC], automatically populating ipd
- descriptors [ODBC], allocating and freeing
- ipd [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1184a7d8-d557-4140-843b-6633ae6deacc
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d637ddfebc0563ed2591740498d519f91e34321e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="automatic-population-of-the-ipd"></a>Автоматическое заполнение IPD
Некоторые драйверы поддерживают параметр полях IPD после параметризованный запрос подготовлен. Поля дескриптора автоматически заполняются сведениями о параметре, включая тип данных, точность, масштаб и другие характеристики. Это эквивалентно поддержки **SQLDescribeParam**. Если нет возможности для обнаружения, например при выполнении нерегламентированного запроса с параметрами, которые приложение не знает о эти сведения можно особенно полезны для приложения.  
  
 Приложение определяет, поддерживает ли драйвер автоматическое заполнение путем вызова **SQLGetConnectAttr** с *атрибута* из SQL_ATTR_AUTO_IPD. Если возвращается SQL_TRUE, драйвер поддерживает его и приложения можно включить, установив атрибут инструкции SQL_ATTR_ENABLE_AUTO_IPD значение SQL_TRUE.  
  
 Если автоматическое заполнение поддерживается и включен, драйвер заполняет поля IPD после инструкции SQL, содержащих маркеры параметров был подготовлен с помощью вызова **SQLPrepare**. Приложения могут получать данные этого путем вызова **SQLGetDescField** или **SQLGetDescRec**, или **SQLDescribeParam**. Приложение может использовать данные для привязки наиболее подходящий буфер приложения, для параметра или для указания преобразования данных для него.  
  
 Автоматическое заполнение IPD может привести к снижению производительности. Приложения могут выключить ее путем присвоения атрибут инструкции SQL_ATTR_ENABLE_AUTO_IPD SQL_FALSE (значение по умолчанию).

