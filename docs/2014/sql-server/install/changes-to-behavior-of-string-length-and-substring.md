---
title: Изменения в работе функций длины строки и подстроки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 2119b7ba-2e52-44bf-ac57-82c2d46a48ff
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7d5fad3b875e781f7682f7e381dbcd4b2db1b3b4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48202890"
---
# <a name="changes-to-behavior-of-string-length-and-substring"></a>Изменения в работе функций длины строки и подстроки
  [Функция string-length &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-string-length) и [substring, функция &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-substring) функции могут возвращать разные результаты при использовании баз данных XML, содержащих суррогатные символы.  
  
## <a name="description"></a>Описание  
 Если база данных настроена на совместимость с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], поведение [функция string-length &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-string-length) и [substring, функция &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-substring) функции изменения, при работе с символами Юникода. Каждый дополнительный символ Юникода, определяемый по кодовой точке больше чем U+FFFF, считается в этих функциях одним символом, а не двумя, как было в предыдущих версиях.  
  
 Дополнительные сведения о суррогатных символах см. в разделе [Суррогаты и дополнительные символы](http://go.microsoft.com/fwlink/?LinkId=178317).  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
