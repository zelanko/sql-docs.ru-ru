---
title: Проверка поддержки функций и изменчивости Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], feature support and variability
- interoperability [ODBC], writing interoperable applications
- feature support in interoperable applications [ODBC]
- feature variability in interoperable applications [ODBC]
ms.assetid: ff45f220-9b8b-4c44-82f8-a8e9913fffea
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 47f16160c05d1c410e3889f0bb857befe88df5b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299174"
---
# <a name="checking-feature-support-and-variability"></a>Проверка поддержки и изменчивости функций
Чтобы проверить поддержку и изменчивость функций, приложения, как правило, вызывают **S'LGetInfo,** **S'LGetФункции**и **S'LGetTypeInfo**. Хорошим стартовым местом является aPI драйвера и уровень соответствия грамматики S'L. В них описывают широкие уровни поддержки функций. Затем приложение может вызыватьs **s'LGetInfo** с другими опциями для определения поддержки или изменчивости необходимых ей функций, **s'LGetOther,** чтобы определить, поддерживаются ли функции, необходимые для этого за пределами уровня возврата, и **S'LGetTypeInfo** для определения того, какие типы данных S'L поддерживаются.  
  
 Приложение может определить, поддерживается ли атрибут оператора или соединения, вызывая с этим атрибутом **s'LSetStmtAttr** или **S'LSetConnectAttr.** Если функция возвращается SQL_SUCCESS или SQL_SUCCESS_WITH_INFO, атрибут поддерживается; если он возвращает SQL_ERROR и S'LSTATE HYC00 (нереализованная функция не реализована), атрибут не поддерживается.  
  
 Приложения также могут определить ограниченный объем информации перед подключением к драйверу, позвонив по **s'LDrivers.**
