---
title: Изменения в работе функций длины строки и подстроки | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2119b7ba-2e52-44bf-ac57-82c2d46a48ff
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3bdc5e23a18b1b182703a1773dc8476eda8d4b14
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188965"
---
# <a name="changes-to-behavior-of-string-length-and-substring"></a>Изменения в работе функций длины строки и подстроки
  [Длины строки функция &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-string-length) и [substring, функция &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-substring) функции могут возвращать разные результаты при использовании баз данных XML, которые содержат суррогатные символы.  
  
## <a name="description"></a>Описание  
 Если база данных настроена на совместимость с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], поведение [длины строки функция &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-string-length) и [substring, функция &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-substring) изменения функций при работе с дополнительными символами Юникода. Каждый дополнительный символ Юникода, определяемый по кодовой точке больше чем U+FFFF, считается в этих функциях одним символом, а не двумя, как было в предыдущих версиях.  
  
 Дополнительные сведения о суррогатных символах см. в разделе [Суррогаты и дополнительные символы](http://go.microsoft.com/fwlink/?LinkId=178317).  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
