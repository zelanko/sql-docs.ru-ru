---
title: Автоматическое заполнение IPD | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- automatically populating ipd [ODBC]
- descriptors [ODBC], automatically populating ipd
- descriptors [ODBC], allocating and freeing
- ipd [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1184a7d8-d557-4140-843b-6633ae6deacc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3d127e2da3397e96059c7d04305a983766ca1db6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63198335"
---
# <a name="automatic-population-of-the-ipd"></a>Автоматическое заполнение IPD
Некоторые драйверы можно настроить поля IPD после подготовки параметризованного запроса. Поля дескриптора автоматически заполняются данными о параметре, включая тип данных, точность, масштаб и другие характеристики. Это эквивалентно поддержкой **SQLDescribeParam**. Эта информация может быть особенно ценна для приложения, когда он находится в другой способ обнаружить его, например когда нерегламентированный запрос выполняется с параметрами, которые приложение не знает о.  
  
 Приложение определяет, поддерживает ли драйвер автоматическое заполнение, вызвав **SQLGetConnectAttr** с *атрибут* из SQL_ATTR_AUTO_IPD. Если возвращается SQL_TRUE, драйвер поддерживает его, и приложения можно включить, установив атрибут инструкции SQL_ATTR_ENABLE_AUTO_IPD задано значение SQL_TRUE.  
  
 При автоматическом заполнении поддерживается и включен, драйвер заполняет поля IPD после инструкции SQL, содержащих маркеры параметров был подготовлен с помощью вызова **SQLPrepare**. Приложение может получить эту информацию, вызвав **SQLGetDescField** или **SQLGetDescRec**, или **SQLDescribeParam**. Приложение может использовать сведения о наиболее подходящий буфер приложения, для параметра или задать преобразование данных для него.  
  
 Автоматическое заполнение IPD может привести к снижению производительности. Приложения могут выключить ее путем присвоения атрибут инструкции SQL_ATTR_ENABLE_AUTO_IPD SQL_FALSE (значение по умолчанию).
